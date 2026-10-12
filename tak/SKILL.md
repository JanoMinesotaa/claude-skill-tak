---
name: tak
description: Odpowiada wyłącznie TAK / NIE / TRUDNO STWIERDZIĆ na pytania zadane w tym samym prompcie. Bez uzasadnień, bez wstępu, bez rozwinięcia. Wywoływane tylko przez użytkownika komendą /tak.
disable-model-invocation: true
argument-hint: "<pytanie, na które da się odpowiedzieć tak lub nie>"
---
Last reviewed: 2026-09-10

# /tak

Użytkownik zadał pytanie i chce werdyktu, nie wywodu.

## Jedyna dozwolona odpowiedź

Dokładnie jedno z trzech, wielkimi literami:

- **TAK**
- **NIE**
- **TRUDNO STWIERDZIĆ**

Nic więcej. Żadnego zdania przed, żadnego po.

## Zasady

1. **Jedno pytanie → jedno słowo.** Cała odpowiedź to `TAK`, `NIE` albo `TRUDNO STWIERDZIĆ`.

2. **Kilka pytań → numerowana lista**, jeden werdykt na pozycję, w kolejności zadania. Bez powtarzania treści pytań:
   ```
   1. TAK
   2. NIE
   3. TRUDNO STWIERDZIĆ
   ```

3. **Kiedy TRUDNO STWIERDZIĆ:** gdy odpowiedź zależy od warunków, gdy brakuje danych do rozstrzygnięcia, gdy pytanie nie jest rozstrzygalne binarnie. To pełnoprawna odpowiedź, nie unik - ale nie jest domyślna. Jeśli da się rozstrzygnąć, rozstrzygnij.

4. **Sprawdź, zanim odpowiesz.** Skrót dotyczy formy odpowiedzi, nie pracy pod nią. Jeśli werdykt zależy od stanu na dysku, w repo albo w sieci - sprawdź to narzędziami, a potem wypluj jedno słowo. Narzędzia wolno uruchamiać; komentować wyników nie.

5. **Tryb jednorazowy.** Obowiązuje tylko tę jedną odpowiedź. Następny prompt bez `/tak` wraca do normalnego stylu.

## Wyjątki - tylko te trzy

1. **Brak pytania w prompcie.** Odpowiedz: `BRAK PYTANIA`.
2. **Pytanie o wykonanie czegoś nieodwracalnego** (kasowanie, nadpisanie, wysłanie na zewnątrz). Nie odpowiadaj jednym słowem - to sytuacja, w której trzeba dopytać.
3. **Użytkownik prosi o uzasadnienie w tym samym prompcie** (np. "/tak czy X? uzasadnij"). Wtedy: werdykt w pierwszej linii, jedno zdanie pod spodem. Nic więcej.

## Czego nie robić

- Nie dopisywać "ale", "chociaż", "zależy od"
- Nie tłumaczyć werdyktu
- Nie proponować kolejnego kroku
- Nie pytać, czy rozwinąć
