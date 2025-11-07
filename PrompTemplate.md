# ✉️ Úloha – Flex Prompt Template pro generování e-mailu o doručení objednávky

## 🎯 Cíl úlohy
Vaším cílem je vytvořit **Flex Prompt Template**, která dokáže automaticky vygenerovat e-mail zákazníkovi s informací o doručení jeho objednávky.

Prompt bude mít **dva vstupy:**
- `Case` – obsahuje dotaz zákazníka (např. e-mail nebo zprávu)
- `Order` – obsahuje číslo objednávky a datum objednání (`EffectiveDate`)

---

## 🧩 Zadání krok za krokem

### 1️⃣ Vytvořte nový Prompt Template
- Typ: **Flex**
- Vstupy: Case a Order

### 2️⃣ Úkol – připravte Prompt, který:

- Vygeneruje e-mail podle následující šablony:  

Subject: Your order [OrderNumber] – delivery information

Body:
Dear [CustomerName],

Thank you for contacting us regarding your order [OrderNumber].

According to our records, your order was placed on [OrderDate].
Based on our delivery policy, your order is expected to be delivered within 3–5 business days after this date.
Your estimated delivery window is between [DeliveryStartDate] and [DeliveryEndDate].

If you have any further questions, please reply to this email.

Kind regards,
Support Team

---

### 3️⃣ Požadavky na funkčnost

- Vstupy do e-mailu musí pocházet z **Case** a **Order**:
  - `[OrderNumber]` = číslo objednávky z objektu Order  
  - `[OrderDate]` = pole `Order.EffectiveDate`
  - `[CustomerName]` = jméno kontaktu z `Case.Contact.FirstName`

- Prompt Template musí **sama vypočítat**:
  - `[DeliveryStartDate]` = 3 dny po `Order.EffectiveDate`  
  - `[DeliveryEndDate]` = 5 dní po `Order.EffectiveDate`  
  - Formát datumu: `DD.MM.YYYY`  
  - Víkendy se počítají jako běžné dny

- E-mail musí být **plně vyplněný** (žádné chybějící placeholdery)
- AI **nesmí měnit text šablony**, jen doplňuje hodnoty
- Odpověď musí být **v angličtině**

---

### 4️⃣ Testování

Po uložení Prompt Template klikněte na **Preview** a vyzkoušejte ji s testovacími daty:
- Vyberte libovolný Case a Order z dat vygenerovaných pomocí `dummydata.script`
- Ověřte, že se e-mail správně doplňuje a že datum doručení odpovídá logice +3 a +5 dní

---

## 💡 Tipy
- Přemýšlejte, jak vysvětlit modelu, aby sám „pochopil“, jak má datum zpracovat a přičíst k němu 3 a 5 dní.  
- Zkuste do promptu přidat krátká pravidla (např. „calculate 3 and 5 days after the input date“)  
- Pokud bude výstup nejednotný, zvažte, jak lépe popsat formátování dat nebo strukturu výstupu.  
---

## ✅ Splněno, pokud:
- Prompt funguje s Case a Order vstupem  
- Vypočítává správné doručovací datumy  
- Vygenerovaný e-mail přesně odpovídá šabloně  
- AI zachovává strukturu a tón e-mailu beze změny
