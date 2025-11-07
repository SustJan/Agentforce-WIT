# 🧠 Agentforce Workshop – Zadání pro Employee Agenta

## 🎯 Cíl
V tomto cvičení si každý účastník vytvoří vlastního **Employee Agenta**, který pomůže uživatelům Salesforce rychle najít odpovědi na zákaznické dotazy a zároveň automaticky navrhne odpověď na e-mail.

---

## 🧩 Úloha 1 – General FAQ

### Cíl
Vytvořte **General FAQ Topic**, který bude umět odpovídat na otázky o dodání, vrácení zboží a reklamacích podle informací uložených v nahraném **PDF souboru**.

### Postup
1. Spusťte připravený **Apex skript** (k dispozici v GitHubu) v **Developer Console → Execute Anonymous**.  
   Tento skript vytvoří ukázková data:
   - **Accounts**, **Contacts**, **Contracts**, **Orders**
   - Několik **Case** záznamů (dotazy od zákazníků) – texty dotazů najdete v poli *Description*

2. Stáhněte si **Return_and_Delivery_FAQ.pdf**. nebo vytvořte pdf soubor pro FAQ.  
   Tento soubor obsahuje informace o doručení, vrácení a reklamacích (můžete použít připravený soubor v GitHubu nebo si vytvořit vlastní).

3. Nahrajte tento PDF soubor do Salesforce jako **Data Library resource** v Agentforce Data Library v Setupe.

4. Vytvořte nového **Employee Agenta** v Agentforce:
   - Přidejte nový **Topic** s názvem `General FAQ`
   - Do topicu vložte akci **Answer Questions With Knowledge**

5. Pridejte vašemu uživateli správné Permission sety (Data Cloud User...)

6. Otestujte agenta dotazy:
   - „How long does it take for a package to be delivered?“  
   - „What should a return package contain?“  
   - „When am I eligible for a complaint?“

**Cíl:** Agent musí dokázat správně odpovědět podle informací z PDF souboru.

---

## 🧩 Úloha 2 – Návrh e-mailové odpovědi (Case Response)

### Cíl
Vytvořte druhý topic, který dokáže analyzovat **Case** záznam a vygenerovat návrh odpovědi pro zákazníka (draft e-mailu).

### Postup
1. Přidejte nový topic s názvem **Case Response**.

3. Použij vhodné actions.

2. Agent by měl reagovat na dotazy jako:
   - „Draft email response“
   - „Please prepare a reply for this customer“

4. Příklady očekávaných odpovědí:
   - **Vrácení zboží:**  
     „Dear Emily, you may return your order within 14 days if unused and in original packaging.“

**Cíl:** Agent musí z Case záznamu pochopit kontext a vytvořit návrh vhodného e-mailu.

Tip: 
- Existuje Standard action **Summarize Record** a **Draft or Revise Email**
---

## 🧩 Úloha 3 – Práce s objednávkami (Order Data)

### Cíl
Rozšiřte předchozí topic **Case Response** tak, aby agent dokázal odpovědět na dotazy týkající se konkrétní objednávky.  
Pokud zákazník napíše například *„Delivery date for order 00001234“*, agent musí:
- Najít odpovídající **Order** záznam v Salesforce
- Získat jeho datum `EffectiveDate`
- Vypočítat a napsat přibližný termín dodání (3–5 dnů po Effective Date)

### Tipy pro dokončení úlohy
- Použijte **context variables**, aby agent věděl, se kterým Order number pracuje.  
- Můžete vytvořit jednoduchý **Flow**, který:
  - Najde odpovídající Order záznam
  - Vrátí hodnotu `EffectiveDate` zpět agentovi  
- Pomoci může i **Summary Record Action**, která vytáhne číslo objednávky přímo z textu Case.
- Každý účastník může použít vlastní přístup – důležité je, aby řešení fungovalo a agent dokázal najít objednávku a vygenerovat správnou odpověď.

### Příklad výstupu
> „Dear John, your order 00001234 is expected to be delivered within 3–5 business days after November 3, 2025.“

---

## 🚀 Bonusová výzva

Pokud se vám podaří dokončit všechny tři úlohy a váš agent funguje správně,  
zkuste vymyslet vlastní rozšíření.

---

## 🧰 Pomůcky

- **Připravený PDF soubor:** `Return_and_Delivery_FAQ.pdf` (v repozitáři GitHub)
- **Apex skript:** `dummydata.script` (v repozitáři GitHub)
- **Oficiální dokumentace:** [Agentforce Developer Workshop](https://developer.salesforce.com/docs)

---

## ✅ Cíl workshopu
Na konci dne by měl mít každý účastník funkčního **Employee Agenta**,  
který dokáže:
- Číst informace z nahraných dokumentů (PDF v Data Library),
- Rozpoznat typ zákaznického dotazu,
- Automaticky navrhnout odpověď e-mailu založenou na datech ze Salesforce.
