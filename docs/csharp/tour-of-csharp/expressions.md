---
title: C# ifadeleri - C# dili turu
description: "C# dili yapı taşlarını şunlardır: ifadeleri, işlenen ve işleçler"
keywords: ".NET, csharp, ifade, işleç, işleç"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 7b7e321e6554818924a8a2b68afa4c787807bcba
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="expressions"></a><span data-ttu-id="82009-104">İfadeler</span><span class="sxs-lookup"><span data-stu-id="82009-104">Expressions</span></span>

<span data-ttu-id="82009-105">*İfadeleri* gelen oluşturulan *işlenenler* ve *işleçleri*.</span><span class="sxs-lookup"><span data-stu-id="82009-105">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="82009-106">İfade işleçleri işlenenlerine uygulamak için hangi işlemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="82009-106">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="82009-107">İşleçler örneklerindendir `+`, `-`, `*`, `/`, ve `new`.</span><span class="sxs-lookup"><span data-stu-id="82009-107">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="82009-108">Değişmez değerler, alanlar, yerel değişkenleri ve ifadeler işlenenler örneklerindendir.</span><span class="sxs-lookup"><span data-stu-id="82009-108">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="82009-109">Bir ifade birden çok işleç içerdiğinde *öncelik* işleçleri tek tek işleçleri değerlendirilir sırasını denetler.</span><span class="sxs-lookup"><span data-stu-id="82009-109">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="82009-110">Örneğin, ifade `x + y * z` olarak değerlendirilir `x + (y * z)` çünkü `*` daha yüksek önceliğe sahip `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="82009-110">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="82009-111">İşleneni aynı önceliğe sahip iki işleç arasında oluştuğunda *birleşim* operatörleri işlemler gerçekleştirilir sırasını denetler:</span><span class="sxs-lookup"><span data-stu-id="82009-111">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="82009-112">Atama işleçleri hariç tüm ikili işleçler şunlardır: *sola ilişkilendirilebilir*, işlemler soldan sağa gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="82009-112">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="82009-113">Örneğin, `x + y + z` olarak değerlendirilir `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="82009-113">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="82009-114">Atama işleçleri ve koşullu işleç (`?:`) olan *sağa ilişkilendirilebilir*, işlemler arasında sağdan sola gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="82009-114">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="82009-115">Örneğin, `x = y = z` olarak değerlendirilir `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="82009-115">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="82009-116">Öncelik ve birleşim parantez kullanılarak denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="82009-116">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="82009-117">Örneğin, `x + y * z` ilk çarpar `y` tarafından `z` ve sonucu ekler `x`, ancak `(x + y) * z` ilk ekler `x` ve `y` ve sonuç olarak çoğaltır `z`.</span><span class="sxs-lookup"><span data-stu-id="82009-117">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="82009-118">Çoğu işleçleri olabilir *aşırı*.</span><span class="sxs-lookup"><span data-stu-id="82009-118">Most operators can be *overloaded*.</span></span> <span data-ttu-id="82009-119">İşleç aşırı yüklemesi, birini veya her ikisini işlenen kullanıcı tanımlı sınıfta veya yapı türü nerede işlemleri için belirtilmesi için kullanıcı tanımlı işleci uygulamaları izin verir.</span><span class="sxs-lookup"><span data-stu-id="82009-119">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="82009-120">Yüksekten en düşüğe öncelik sırasına işleci kategorilerini liste C# ' ın işleçleri, aşağıda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="82009-120">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="82009-121">Aynı kategoride operatörleri eşit önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="82009-121">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="82009-122">Her kategori altında bu ifade türünün açıklaması yanı sıra bu kategorideki ifadeleri listesidir.</span><span class="sxs-lookup"><span data-stu-id="82009-122">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="82009-123">birincil</span><span class="sxs-lookup"><span data-stu-id="82009-123">Primary</span></span>
    - <span data-ttu-id="82009-124">`x.m`: Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="82009-124">`x.m`: Member access</span></span>
    - <span data-ttu-id="82009-125">`x(...)`: Yöntemi ve temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="82009-125">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="82009-126">`x[...]`: Dizi ve dizin oluşturucu erişim</span><span class="sxs-lookup"><span data-stu-id="82009-126">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="82009-127">`x++`: Sonrası artırma</span><span class="sxs-lookup"><span data-stu-id="82009-127">`x++`: Post-increment</span></span>
    - <span data-ttu-id="82009-128">`x--`: Sonrası azaltma</span><span class="sxs-lookup"><span data-stu-id="82009-128">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="82009-129">`new T(...)`: Nesne ve temsilci oluşturma</span><span class="sxs-lookup"><span data-stu-id="82009-129">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="82009-130">`new T(...){...}`: Başlatıcısı ile nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="82009-130">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="82009-131">`new {...}`: Anonim nesne Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="82009-131">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="82009-132">`new T[...]`: Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="82009-132">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="82009-133">`typeof(T)`: Elde <xref:System.Type> nesnesi`T`</span><span class="sxs-lookup"><span data-stu-id="82009-133">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="82009-134">`checked(x)`: Checked bağlamda ifade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="82009-134">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="82009-135">`unchecked(x)`: Denetlenmeyen bağlamda ifade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="82009-135">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="82009-136">`default(T)`: Türü varsayılan değerini edinme`T`</span><span class="sxs-lookup"><span data-stu-id="82009-136">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="82009-137">`delegate {...}`: Anonim işlevi (anonim yöntemi)</span><span class="sxs-lookup"><span data-stu-id="82009-137">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="82009-138">Birli</span><span class="sxs-lookup"><span data-stu-id="82009-138">Unary</span></span>
    - <span data-ttu-id="82009-139">`+x`: Kimlik</span><span class="sxs-lookup"><span data-stu-id="82009-139">`+x`: Identity</span></span>
    - <span data-ttu-id="82009-140">`-x`: Değilleme</span><span class="sxs-lookup"><span data-stu-id="82009-140">`-x`: Negation</span></span>
    - <span data-ttu-id="82009-141">`!x`: Mantıksal olumsuzlaştırma</span><span class="sxs-lookup"><span data-stu-id="82009-141">`!x`: Logical negation</span></span>
    - <span data-ttu-id="82009-142">`~x`: Bit tabanlı değil işlecini</span><span class="sxs-lookup"><span data-stu-id="82009-142">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="82009-143">`++x`: Ön artırma</span><span class="sxs-lookup"><span data-stu-id="82009-143">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="82009-144">`--x`: Ön azaltma</span><span class="sxs-lookup"><span data-stu-id="82009-144">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="82009-145">`(T)x`: Açıkça dönüştürme `x` yazmak için`T`</span><span class="sxs-lookup"><span data-stu-id="82009-145">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="82009-146">`await x`: Zaman uyumsuz olarak bekleyin `x` tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="82009-146">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="82009-147">Çarpma</span><span class="sxs-lookup"><span data-stu-id="82009-147">Multiplicative</span></span>
    - <span data-ttu-id="82009-148">`x * y`: Çarpma</span><span class="sxs-lookup"><span data-stu-id="82009-148">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="82009-149">`x / y`: Bölme</span><span class="sxs-lookup"><span data-stu-id="82009-149">`x / y`: Division</span></span>
    - <span data-ttu-id="82009-150">`x % y`: Kalan</span><span class="sxs-lookup"><span data-stu-id="82009-150">`x % y`: Remainder</span></span>
* <span data-ttu-id="82009-151">ADDITIVE</span><span class="sxs-lookup"><span data-stu-id="82009-151">Additive</span></span>
    - <span data-ttu-id="82009-152">`x + y`: Eklenmesi, dize birleştirme, temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="82009-152">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="82009-153">`x – y`: Çıkarma, temsilci kaldırma</span><span class="sxs-lookup"><span data-stu-id="82009-153">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="82009-154">Kaydırma</span><span class="sxs-lookup"><span data-stu-id="82009-154">Shift</span></span>
    - <span data-ttu-id="82009-155">`x << y`: Shift sol</span><span class="sxs-lookup"><span data-stu-id="82009-155">`x << y`: Shift left</span></span>
    - <span data-ttu-id="82009-156">`x >> y`: Sağa kaydırma</span><span class="sxs-lookup"><span data-stu-id="82009-156">`x >> y`: Shift right</span></span>
* <span data-ttu-id="82009-157">İlişkisel ve türü test etme</span><span class="sxs-lookup"><span data-stu-id="82009-157">Relational and type testing</span></span>
    - <span data-ttu-id="82009-158">`x < y`: Küçüktür</span><span class="sxs-lookup"><span data-stu-id="82009-158">`x < y`: Less than</span></span>
    - <span data-ttu-id="82009-159">`x > y`: Büyüktür</span><span class="sxs-lookup"><span data-stu-id="82009-159">`x > y`: Greater than</span></span>
    - <span data-ttu-id="82009-160">`x <= y`: Küçüktür veya eşittir</span><span class="sxs-lookup"><span data-stu-id="82009-160">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="82009-161">`x >= y`: Büyüktür veya eşittir</span><span class="sxs-lookup"><span data-stu-id="82009-161">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="82009-162">`x is T`: Dönüş `true` varsa `x` olan bir `T`, `false` Aksi takdirde</span><span class="sxs-lookup"><span data-stu-id="82009-162">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="82009-163">`x as T`: Dönüş `x` olarak yazılan `T`, veya `null` varsa `x` değil bir`T`</span><span class="sxs-lookup"><span data-stu-id="82009-163">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="82009-164">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="82009-164">Equality</span></span>
    - <span data-ttu-id="82009-165">`x == y`: Eşit</span><span class="sxs-lookup"><span data-stu-id="82009-165">`x == y`: Equal</span></span>
    - <span data-ttu-id="82009-166">`x != y`: Eşit değil</span><span class="sxs-lookup"><span data-stu-id="82009-166">`x != y`: Not equal</span></span>
* <span data-ttu-id="82009-167">Mantıksal VE</span><span class="sxs-lookup"><span data-stu-id="82009-167">Logical AND</span></span>
    - <span data-ttu-id="82009-168">`x & y`: Tamsayı Bitsel ve, Boole mantıksal ve</span><span class="sxs-lookup"><span data-stu-id="82009-168">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="82009-169">Mantıksal XOR</span><span class="sxs-lookup"><span data-stu-id="82009-169">Logical XOR</span></span>
    - <span data-ttu-id="82009-170">`x ^ y`: Bit düzeyinde XOR tamsayı, boolean mantıksal XOR</span><span class="sxs-lookup"><span data-stu-id="82009-170">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="82009-171">Mantıksal VEYA</span><span class="sxs-lookup"><span data-stu-id="82009-171">Logical OR</span></span>
    - <span data-ttu-id="82009-172">`x | y`: Tamsayı Bitsel veya boolean mantıksal OR</span><span class="sxs-lookup"><span data-stu-id="82009-172">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="82009-173">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="82009-173">Conditional AND</span></span>
    - <span data-ttu-id="82009-174">`x && y`: Hesaplar `y` yalnızca `x` değil`false`</span><span class="sxs-lookup"><span data-stu-id="82009-174">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="82009-175">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="82009-175">Conditional OR</span></span>
    - <span data-ttu-id="82009-176">`x || y`: Hesaplar `y` yalnızca `x` değil`true`</span><span class="sxs-lookup"><span data-stu-id="82009-176">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="82009-177">Null birleşim</span><span class="sxs-lookup"><span data-stu-id="82009-177">Null coalescing</span></span>
    - <span data-ttu-id="82009-178">`x ?? y`: Değerlendiren `y` varsa `x` için null `x` Aksi takdirde</span><span class="sxs-lookup"><span data-stu-id="82009-178">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="82009-179">Koşullu</span><span class="sxs-lookup"><span data-stu-id="82009-179">Conditional</span></span>
    - <span data-ttu-id="82009-180">`x ? y : z`: Hesaplar `y` varsa `x` olan `true`, `z` varsa `x` olduğu`false`</span><span class="sxs-lookup"><span data-stu-id="82009-180">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="82009-181">Atama veya anonim işlevi</span><span class="sxs-lookup"><span data-stu-id="82009-181">Assignment or anonymous function</span></span>
    - <span data-ttu-id="82009-182">`x = y`: Atama</span><span class="sxs-lookup"><span data-stu-id="82009-182">`x = y`: Assignment</span></span>
    - <span data-ttu-id="82009-183">`x op= y`: Bileşik atama; desteklenen işleçler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="82009-183">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="82009-184">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="82009-184">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="82009-185">`(T x) => y`: Anonim işlevi (lambda ifadesi)</span><span class="sxs-lookup"><span data-stu-id="82009-185">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="82009-186">[Önceki](types-and-variables.md)
[sonraki](statements.md)</span><span class="sxs-lookup"><span data-stu-id="82009-186">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
