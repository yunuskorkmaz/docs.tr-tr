---
title: C# ifadeleri - C# dili turu
description: 'C# dili yapı taşlarını şunlardır: ifadeleri, işlenen ve işleçler'
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 8fa1c5d0464644b26eb457bca8ecaf007c288f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352311"
---
# <a name="expressions"></a><span data-ttu-id="5b829-103">İfadeler</span><span class="sxs-lookup"><span data-stu-id="5b829-103">Expressions</span></span>

<span data-ttu-id="5b829-104">*İfadeleri* gelen oluşturulan *işlenenler* ve *işleçleri*.</span><span class="sxs-lookup"><span data-stu-id="5b829-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="5b829-105">İfade işleçleri işlenenlerine uygulamak için hangi işlemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b829-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="5b829-106">İşleçler örneklerindendir `+`, `-`, `*`, `/`, ve `new`.</span><span class="sxs-lookup"><span data-stu-id="5b829-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="5b829-107">Değişmez değerler, alanlar, yerel değişkenleri ve ifadeler işlenenler örneklerindendir.</span><span class="sxs-lookup"><span data-stu-id="5b829-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="5b829-108">Bir ifade birden çok işleç içerdiğinde *öncelik* işleçleri tek tek işleçleri değerlendirilir sırasını denetler.</span><span class="sxs-lookup"><span data-stu-id="5b829-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="5b829-109">Örneğin, ifade `x + y * z` olarak değerlendirilir `x + (y * z)` çünkü `*` daha yüksek önceliğe sahip `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="5b829-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="5b829-110">İşleneni aynı önceliğe sahip iki işleç arasında oluştuğunda *birleşim* operatörleri işlemler gerçekleştirilir sırasını denetler:</span><span class="sxs-lookup"><span data-stu-id="5b829-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="5b829-111">Atama işleçleri hariç tüm ikili işleçler şunlardır: *sola ilişkilendirilebilir*, işlemler soldan sağa gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b829-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="5b829-112">Örneğin, `x + y + z` olarak değerlendirilir `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="5b829-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="5b829-113">Atama işleçleri ve koşullu işleç (`?:`) olan *sağa ilişkilendirilebilir*, işlemler arasında sağdan sola gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b829-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="5b829-114">Örneğin, `x = y = z` olarak değerlendirilir `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="5b829-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="5b829-115">Öncelik ve birleşim parantez kullanılarak denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5b829-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="5b829-116">Örneğin, `x + y * z` ilk çarpar `y` tarafından `z` ve sonucu ekler `x`, ancak `(x + y) * z` ilk ekler `x` ve `y` ve sonuç olarak çoğaltır `z`.</span><span class="sxs-lookup"><span data-stu-id="5b829-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="5b829-117">Çoğu işleçleri olabilir *aşırı*.</span><span class="sxs-lookup"><span data-stu-id="5b829-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="5b829-118">İşleç aşırı yüklemesi, birini veya her ikisini işlenen kullanıcı tanımlı sınıfta veya yapı türü nerede işlemleri için belirtilmesi için kullanıcı tanımlı işleci uygulamaları izin verir.</span><span class="sxs-lookup"><span data-stu-id="5b829-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="5b829-119">Yüksekten en düşüğe öncelik sırasına işleci kategorilerini liste C# ' ın işleçleri, aşağıda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b829-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="5b829-120">Aynı kategoride operatörleri eşit önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5b829-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="5b829-121">Her kategori altında bu ifade türünün açıklaması yanı sıra bu kategorideki ifadeleri listesidir.</span><span class="sxs-lookup"><span data-stu-id="5b829-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="5b829-122">birincil</span><span class="sxs-lookup"><span data-stu-id="5b829-122">Primary</span></span>
    - <span data-ttu-id="5b829-123">`x.m`: Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="5b829-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="5b829-124">`x(...)`: Yöntemi ve temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="5b829-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="5b829-125">`x[...]`: Dizi ve dizin oluşturucu erişim</span><span class="sxs-lookup"><span data-stu-id="5b829-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="5b829-126">`x++`: Sonrası artırma</span><span class="sxs-lookup"><span data-stu-id="5b829-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="5b829-127">`x--`: Sonrası azaltma</span><span class="sxs-lookup"><span data-stu-id="5b829-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="5b829-128">`new T(...)`: Nesne ve temsilci oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b829-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="5b829-129">`new T(...){...}`: Başlatıcısı ile nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b829-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="5b829-130">`new {...}`: Anonim nesne Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="5b829-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="5b829-131">`new T[...]`: Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b829-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="5b829-132">`typeof(T)`: Elde <xref:System.Type> nesnesi `T`</span><span class="sxs-lookup"><span data-stu-id="5b829-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="5b829-133">`checked(x)`: Checked bağlamda ifade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="5b829-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="5b829-134">`unchecked(x)`: Denetlenmeyen bağlamda ifade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="5b829-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="5b829-135">`default(T)`: Türü varsayılan değerini edinme `T`</span><span class="sxs-lookup"><span data-stu-id="5b829-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="5b829-136">`delegate {...}`: Anonim işlevi (anonim yöntemi)</span><span class="sxs-lookup"><span data-stu-id="5b829-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="5b829-137">Birli</span><span class="sxs-lookup"><span data-stu-id="5b829-137">Unary</span></span>
    - <span data-ttu-id="5b829-138">`+x`: Kimlik</span><span class="sxs-lookup"><span data-stu-id="5b829-138">`+x`: Identity</span></span>
    - <span data-ttu-id="5b829-139">`-x`: Değilleme</span><span class="sxs-lookup"><span data-stu-id="5b829-139">`-x`: Negation</span></span>
    - <span data-ttu-id="5b829-140">`!x`: Mantıksal olumsuzlaştırma</span><span class="sxs-lookup"><span data-stu-id="5b829-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="5b829-141">`~x`: Bit tabanlı değil işlecini</span><span class="sxs-lookup"><span data-stu-id="5b829-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="5b829-142">`++x`: Ön artırma</span><span class="sxs-lookup"><span data-stu-id="5b829-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="5b829-143">`--x`: Ön azaltma</span><span class="sxs-lookup"><span data-stu-id="5b829-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="5b829-144">`(T)x`: Açıkça dönüştürme `x` yazmak için `T`</span><span class="sxs-lookup"><span data-stu-id="5b829-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="5b829-145">`await x`: Zaman uyumsuz olarak bekleyin `x` tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="5b829-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="5b829-146">Çarpma</span><span class="sxs-lookup"><span data-stu-id="5b829-146">Multiplicative</span></span>
    - <span data-ttu-id="5b829-147">`x * y`: Çarpma</span><span class="sxs-lookup"><span data-stu-id="5b829-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="5b829-148">`x / y`: Bölme</span><span class="sxs-lookup"><span data-stu-id="5b829-148">`x / y`: Division</span></span>
    - <span data-ttu-id="5b829-149">`x % y`: Kalan</span><span class="sxs-lookup"><span data-stu-id="5b829-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="5b829-150">ADDITIVE</span><span class="sxs-lookup"><span data-stu-id="5b829-150">Additive</span></span>
    - <span data-ttu-id="5b829-151">`x + y`: Eklenmesi, dize birleştirme, temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="5b829-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="5b829-152">`x – y`: Çıkarma, temsilci kaldırma</span><span class="sxs-lookup"><span data-stu-id="5b829-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="5b829-153">Kaydırma</span><span class="sxs-lookup"><span data-stu-id="5b829-153">Shift</span></span>
    - <span data-ttu-id="5b829-154">`x << y`: Shift sol</span><span class="sxs-lookup"><span data-stu-id="5b829-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="5b829-155">`x >> y`: Sağa kaydırma</span><span class="sxs-lookup"><span data-stu-id="5b829-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="5b829-156">İlişkisel ve türü test etme</span><span class="sxs-lookup"><span data-stu-id="5b829-156">Relational and type testing</span></span>
    - <span data-ttu-id="5b829-157">`x < y`: Küçüktür</span><span class="sxs-lookup"><span data-stu-id="5b829-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="5b829-158">`x > y`: Büyüktür</span><span class="sxs-lookup"><span data-stu-id="5b829-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="5b829-159">`x <= y`: Küçüktür veya eşittir</span><span class="sxs-lookup"><span data-stu-id="5b829-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="5b829-160">`x >= y`: Büyüktür veya eşittir</span><span class="sxs-lookup"><span data-stu-id="5b829-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="5b829-161">`x is T`: Dönüş `true` varsa `x` olan bir `T`, `false` Aksi takdirde</span><span class="sxs-lookup"><span data-stu-id="5b829-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="5b829-162">`x as T`: Dönüş `x` olarak yazılan `T`, veya `null` varsa `x` değil bir `T`</span><span class="sxs-lookup"><span data-stu-id="5b829-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="5b829-163">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="5b829-163">Equality</span></span>
    - <span data-ttu-id="5b829-164">`x == y`: Eşit</span><span class="sxs-lookup"><span data-stu-id="5b829-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="5b829-165">`x != y`: Eşit değil</span><span class="sxs-lookup"><span data-stu-id="5b829-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="5b829-166">Mantıksal VE</span><span class="sxs-lookup"><span data-stu-id="5b829-166">Logical AND</span></span>
    - <span data-ttu-id="5b829-167">`x & y`: Tamsayı Bitsel ve, Boole mantıksal ve</span><span class="sxs-lookup"><span data-stu-id="5b829-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="5b829-168">Mantıksal XOR</span><span class="sxs-lookup"><span data-stu-id="5b829-168">Logical XOR</span></span>
    - <span data-ttu-id="5b829-169">`x ^ y`: Bit düzeyinde XOR tamsayı, boolean mantıksal XOR</span><span class="sxs-lookup"><span data-stu-id="5b829-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="5b829-170">Mantıksal VEYA</span><span class="sxs-lookup"><span data-stu-id="5b829-170">Logical OR</span></span>
    - <span data-ttu-id="5b829-171">`x | y`: Tamsayı Bitsel veya boolean mantıksal OR</span><span class="sxs-lookup"><span data-stu-id="5b829-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="5b829-172">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="5b829-172">Conditional AND</span></span>
    - <span data-ttu-id="5b829-173">`x && y`: Hesaplar `y` yalnızca `x` değil `false`</span><span class="sxs-lookup"><span data-stu-id="5b829-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="5b829-174">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="5b829-174">Conditional OR</span></span>
    - <span data-ttu-id="5b829-175">`x || y`: Hesaplar `y` yalnızca `x` değil `true`</span><span class="sxs-lookup"><span data-stu-id="5b829-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="5b829-176">Null birleşim</span><span class="sxs-lookup"><span data-stu-id="5b829-176">Null coalescing</span></span>
    - <span data-ttu-id="5b829-177">`x ?? y`: Değerlendiren `y` varsa `x` için null `x` Aksi takdirde</span><span class="sxs-lookup"><span data-stu-id="5b829-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="5b829-178">Koşullu</span><span class="sxs-lookup"><span data-stu-id="5b829-178">Conditional</span></span>
    - <span data-ttu-id="5b829-179">`x ? y : z`: Hesaplar `y` varsa `x` olan `true`, `z` varsa `x` olduğu `false`</span><span class="sxs-lookup"><span data-stu-id="5b829-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="5b829-180">Atama veya anonim işlevi</span><span class="sxs-lookup"><span data-stu-id="5b829-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="5b829-181">`x = y`: Atama</span><span class="sxs-lookup"><span data-stu-id="5b829-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="5b829-182">`x op= y`: Bileşik atama; desteklenen işleçler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5b829-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="5b829-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="5b829-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="5b829-184">`(T x) => y`: Anonim işlevi (lambda ifadesi)</span><span class="sxs-lookup"><span data-stu-id="5b829-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="5b829-185">[Önceki](types-and-variables.md)
[sonraki](statements.md)</span><span class="sxs-lookup"><span data-stu-id="5b829-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
