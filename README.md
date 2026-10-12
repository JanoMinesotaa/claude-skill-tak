# /tak - skill do Claude Code

> **EN:** `/tak <question>` is a Claude Code skill that answers a yes/no question with exactly one
> word: `TAK` (yes), `NIE` (no) or `TRUDNO STWIERDZIĆ` (hard to say). No preamble, no explanation.
> The skill text and the verdict words are in Polish. Install: see below.

Skill do [Claude Code](https://claude.com/claude-code). Wpisujesz `/tak <pytanie>`, a Claude
odpowiada **jednym słowem** - bez wstępu, bez uzasadnienia, bez pytania, czy rozwinąć.

## Co robi

Odpowiedź to dokładnie jedno z trzech:

- **TAK**
- **NIE**
- **TRUDNO STWIERDZIĆ** - gdy odpowiedź zależy od warunków, brakuje danych albo pytania nie da się
  rozstrzygnąć binarnie. To nie jest domyślny unik: jeśli da się rozstrzygnąć, Claude rozstrzyga.

Dodatkowo:

- **Kilka pytań w jednym prompcie** - numerowana lista werdyktów w kolejności zadania.
- **Sprawdza, zanim odpowie.** Skrót dotyczy formy odpowiedzi, nie pracy pod nią. Jeśli werdykt zależy
  od stanu plików, repo albo sieci, Claude to sprawdzi narzędziami i dopiero potem poda słowo.
- **Tryb jednorazowy** - działa tylko na ten jeden prompt. Następna wiadomość bez `/tak` wraca do
  normalnego stylu.
- **Wywołanie tylko ręczne** (`disable-model-invocation: true`) - Claude sam go nie uruchomi.

Trzy wyjątki od zasady „jedno słowo":

1. Brak pytania w prompcie -> `BRAK PYTANIA`.
2. Pytanie o coś nieodwracalnego (kasowanie, nadpisanie, wysłanie na zewnątrz) -> Claude dopytuje
   zamiast odpowiadać jednym słowem.
3. Prosisz o uzasadnienie w tym samym prompcie (`/tak czy X? uzasadnij`) -> werdykt w pierwszej linii
   i jedno zdanie pod spodem.

## Przykłady

```
/tak czy plik package.json istnieje w tym katalogu?
TAK
```

```
/tak 1) czy ten test przechodzi? 2) czy w repo jest plik LICENSE? 3) czy ta biblioteka będzie popularna za 5 lat?
1. NIE
2. TAK
3. TRUDNO STWIERDZIĆ
```

## Instalacja

Skill to jeden plik: `tak/SKILL.md`. Claude Code wczytuje skille osobiste z `~/.claude/skills/`.

**Wariant 1 - klon repo (Terminal):**

```bash
git clone https://github.com/JanoMinesotaa/claude-skill-tak.git
mkdir -p ~/.claude/skills
cp -r claude-skill-tak/tak ~/.claude/skills/tak
```

**Wariant 2 - jedna komenda, bez klonowania (Terminal):**

```bash
mkdir -p ~/.claude/skills/tak && curl -fsSL https://raw.githubusercontent.com/JanoMinesotaa/claude-skill-tak/main/tak/SKILL.md -o ~/.claude/skills/tak/SKILL.md
```

Potem **uruchom nową sesję Claude Code** i wpisz `/tak` z pytaniem.

Instalacja tylko dla jednego projektu: skopiuj folder `tak` do `.claude/skills/` w katalogu projektu
zamiast do `~/.claude/skills/`.

## Odinstalowanie

```bash
rm -rf ~/.claude/skills/tak
```

## Dostosowanie

Treść skilla jest zwykłym markdownem w `tak/SKILL.md`. Możesz zmienić słowa werdyktu (np. na
`YES` / `NO` / `UNCLEAR`) i reguły - wystarczy edytować plik i zacząć nową sesję.

## Licencja

MIT - zobacz [LICENSE](LICENSE).
