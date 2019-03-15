---
title: C#İfadeleri - Turu C# dil
description: ifadeleri ve işlenenleri işleçleri olan yapı taşları C# dil
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 7a7f65eb7ba3da3f9630bbcb92d8578d60d2095d
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846603"
---
# <a name="expressions"></a><span data-ttu-id="b37b4-103">İfadeler</span><span class="sxs-lookup"><span data-stu-id="b37b4-103">Expressions</span></span>

<span data-ttu-id="b37b4-104">*İfadeleri* oluşturulan *işlenenler* ve *işleçleri*.</span><span class="sxs-lookup"><span data-stu-id="b37b4-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="b37b4-105">İfade işleçleri işlenenlere uygulamak için hangi işlemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b37b4-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="b37b4-106">İşleçler örnekler `+`, `-`, `*`, `/`, ve `new`.</span><span class="sxs-lookup"><span data-stu-id="b37b4-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="b37b4-107">Değişmez değerler, alanlar, yerel değişkenleri ve ifadeleri işlenenler örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="b37b4-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="b37b4-108">Bir ifade birden çok işleç içeren *öncelik* işleçleri tek tek işleçler değerlendirilme sırası denetler.</span><span class="sxs-lookup"><span data-stu-id="b37b4-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="b37b4-109">Örneğin, ifade `x + y * z` değerlendirmesinde `x + (y * z)` çünkü `*` işleci daha yüksek önceliğe sahip `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="b37b4-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="b37b4-110">Bir işlenen aynı önceliğe sahip iki işleç arasında gerçekleştiğinde *ilişkilendirilebilirliği* operatörleri işlemleri gerçekleştirilir sırasını denetler:</span><span class="sxs-lookup"><span data-stu-id="b37b4-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="b37b4-111">Atama işleçleri hariç tüm ikili işleçler şunlardır *ilişkilendirilebilir*, yani işlemler soldan sağa doğru gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b37b4-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="b37b4-112">Örneğin, `x + y + z` değerlendirmesinde `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="b37b4-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="b37b4-113">Atama işleçleri ve koşullu işleç (`?:`) olan *sağla ilişkilendirilebilir*, sağdan sola işlemler gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b37b4-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="b37b4-114">Örneğin, `x = y = z` değerlendirmesinde `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="b37b4-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="b37b4-115">Öncelik ve ilişkisellik parantez kullanılarak denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b37b4-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="b37b4-116">Örneğin, `x + y * z` ilk çarpar `y` tarafından `z` ve ardından sonuca ekler `x`, ancak `(x + y) * z` ilk ekler `x` ve `y` ve sonucu çarpan `z`.</span><span class="sxs-lookup"><span data-stu-id="b37b4-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="b37b4-117">Çoğu işleçleri olabilir *aşırı*.</span><span class="sxs-lookup"><span data-stu-id="b37b4-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="b37b4-118">İşleç aşırı yüklemesi, aşağıdakilerden birini veya her iki işlenen kullanıcı tanımlı sınıf veya yapı türü olduğu işlemlerinde belirtilmesi için kullanıcı tanımlı işleç uygulamalarına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b37b4-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="b37b4-119">Aşağıdaki özetler C#'s işleçlerini, en düşük yüksekten öncelik sırasına işleci kategorileri listeleme.</span><span class="sxs-lookup"><span data-stu-id="b37b4-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="b37b4-120">Aynı kategoride işleçleri eşit önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b37b4-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="b37b4-121">Her kategori altında bu ifade türünün açıklaması ile birlikte bu kategorideki ifadeleri listesidir.</span><span class="sxs-lookup"><span data-stu-id="b37b4-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="b37b4-122">Birincil</span><span class="sxs-lookup"><span data-stu-id="b37b4-122">Primary</span></span>
    - <span data-ttu-id="b37b4-123">`x.m`: Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="b37b4-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="b37b4-124">`x(...)`: Yöntem ve temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="b37b4-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="b37b4-125">`x[...]`: Dizi ve dizinleyici erişimi</span><span class="sxs-lookup"><span data-stu-id="b37b4-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="b37b4-126">`x++`: Artırım sonrası</span><span class="sxs-lookup"><span data-stu-id="b37b4-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="b37b4-127">`x--`: Azaltım sonrası</span><span class="sxs-lookup"><span data-stu-id="b37b4-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="b37b4-128">`new T(...)`: Nesne ve temsilci oluşturma</span><span class="sxs-lookup"><span data-stu-id="b37b4-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="b37b4-129">`new T(...){...}`: Başlatıcı ile nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="b37b4-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="b37b4-130">`new {...}`:  Anonim nesne Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="b37b4-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="b37b4-131">`new T[...]`: Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b37b4-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="b37b4-132">`typeof(T)`: Elde <xref:System.Type> nesnesi `T`</span><span class="sxs-lookup"><span data-stu-id="b37b4-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="b37b4-133">`checked(x)`: İşaretli bağlamında ifade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="b37b4-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="b37b4-134">`unchecked(x)`: İşaretlenmemiş bağlamında ifade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="b37b4-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="b37b4-135">`default(T)`: Türünün varsayılan değerini alın `T`</span><span class="sxs-lookup"><span data-stu-id="b37b4-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="b37b4-136">`delegate {...}`: Anonim işlevi (anonim yöntemi)</span><span class="sxs-lookup"><span data-stu-id="b37b4-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="b37b4-137">Birli</span><span class="sxs-lookup"><span data-stu-id="b37b4-137">Unary</span></span>
    - <span data-ttu-id="b37b4-138">`+x`: Kimlik</span><span class="sxs-lookup"><span data-stu-id="b37b4-138">`+x`: Identity</span></span>
    - <span data-ttu-id="b37b4-139">`-x`: Olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="b37b4-139">`-x`: Negation</span></span>
    - <span data-ttu-id="b37b4-140">`!x`: Mantıksal olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="b37b4-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="b37b4-141">`~x`: Bitwise olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="b37b4-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="b37b4-142">`++x`: Artırım öncesi</span><span class="sxs-lookup"><span data-stu-id="b37b4-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="b37b4-143">`--x`: Azaltım öncesi</span><span class="sxs-lookup"><span data-stu-id="b37b4-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="b37b4-144">`(T)x`: Açıkça dönüştürmek `x` yazmak için `T`</span><span class="sxs-lookup"><span data-stu-id="b37b4-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="b37b4-145">`await x`: Zaman uyumsuz olarak bekleyin `x` tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="b37b4-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="b37b4-146">Çarpma</span><span class="sxs-lookup"><span data-stu-id="b37b4-146">Multiplicative</span></span>
    - <span data-ttu-id="b37b4-147">`x * y`: Çarpma</span><span class="sxs-lookup"><span data-stu-id="b37b4-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="b37b4-148">`x / y`: Bölme</span><span class="sxs-lookup"><span data-stu-id="b37b4-148">`x / y`: Division</span></span>
    - <span data-ttu-id="b37b4-149">`x % y`: Kalan</span><span class="sxs-lookup"><span data-stu-id="b37b4-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="b37b4-150">Eklenebilir</span><span class="sxs-lookup"><span data-stu-id="b37b4-150">Additive</span></span>
    - <span data-ttu-id="b37b4-151">`x + y`: Toplama, dize bitiştirme, temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="b37b4-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="b37b4-152">`x – y`: Çıkarma, temsilci kaldırma</span><span class="sxs-lookup"><span data-stu-id="b37b4-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="b37b4-153">Shift</span><span class="sxs-lookup"><span data-stu-id="b37b4-153">Shift</span></span>
    - <span data-ttu-id="b37b4-154">`x << y`: Sola kaydırma</span><span class="sxs-lookup"><span data-stu-id="b37b4-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="b37b4-155">`x >> y`: Sağa kaydırma</span><span class="sxs-lookup"><span data-stu-id="b37b4-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="b37b4-156">İlişkisel ve tür testi</span><span class="sxs-lookup"><span data-stu-id="b37b4-156">Relational and type testing</span></span>
    - <span data-ttu-id="b37b4-157">`x < y`: Küçüktür</span><span class="sxs-lookup"><span data-stu-id="b37b4-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="b37b4-158">`x > y`: Büyüktür</span><span class="sxs-lookup"><span data-stu-id="b37b4-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="b37b4-159">`x <= y`: Küçük veya eşittir</span><span class="sxs-lookup"><span data-stu-id="b37b4-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="b37b4-160">`x >= y`: Büyük veya eşittir</span><span class="sxs-lookup"><span data-stu-id="b37b4-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="b37b4-161">`x is T`: Dönüş `true` varsa `x` olduğu bir `T`, `false` Aksi takdirde</span><span class="sxs-lookup"><span data-stu-id="b37b4-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="b37b4-162">`x as T`: Dönüş `x` olarak yazılan `T`, veya `null` varsa `x` değil bir `T`</span><span class="sxs-lookup"><span data-stu-id="b37b4-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="b37b4-163">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="b37b4-163">Equality</span></span>
    - <span data-ttu-id="b37b4-164">`x == y`: Eşittir</span><span class="sxs-lookup"><span data-stu-id="b37b4-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="b37b4-165">`x != y`: Eşit değildir</span><span class="sxs-lookup"><span data-stu-id="b37b4-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="b37b4-166">Mantıksal VE</span><span class="sxs-lookup"><span data-stu-id="b37b4-166">Logical AND</span></span>
    - <span data-ttu-id="b37b4-167">`x & y`: Tamsayı bitwise ve, boolean mantıksal ve</span><span class="sxs-lookup"><span data-stu-id="b37b4-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="b37b4-168">Mantıksal XOR</span><span class="sxs-lookup"><span data-stu-id="b37b4-168">Logical XOR</span></span>
    - <span data-ttu-id="b37b4-169">`x ^ y`: Tamsayı bitwise XOR, Boolean mantıksal XOR</span><span class="sxs-lookup"><span data-stu-id="b37b4-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="b37b4-170">Mantıksal VEYA</span><span class="sxs-lookup"><span data-stu-id="b37b4-170">Logical OR</span></span>
    - <span data-ttu-id="b37b4-171">`x | y`: Tamsayı bitwise VEYA, boolean mantıksal VEYA</span><span class="sxs-lookup"><span data-stu-id="b37b4-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="b37b4-172">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="b37b4-172">Conditional AND</span></span>
    - <span data-ttu-id="b37b4-173">`x && y`: Değerlendirilen `y` yalnızca `x` değil `false`</span><span class="sxs-lookup"><span data-stu-id="b37b4-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="b37b4-174">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="b37b4-174">Conditional OR</span></span>
    - <span data-ttu-id="b37b4-175">`x || y`: Değerlendirilen `y` yalnızca `x` değil `true`</span><span class="sxs-lookup"><span data-stu-id="b37b4-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="b37b4-176">Null birleşim</span><span class="sxs-lookup"><span data-stu-id="b37b4-176">Null coalescing</span></span>
    - <span data-ttu-id="b37b4-177">`x ?? y`: Değerlendiren `y` varsa `x` için null `x` Aksi takdirde</span><span class="sxs-lookup"><span data-stu-id="b37b4-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="b37b4-178">Koşullu</span><span class="sxs-lookup"><span data-stu-id="b37b4-178">Conditional</span></span>
    - <span data-ttu-id="b37b4-179">`x ? y : z`: Değerlendirir `y` varsa `x` olduğu `true`, `z` varsa `x` olduğu `false`</span><span class="sxs-lookup"><span data-stu-id="b37b4-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="b37b4-180">Atama ve anonim işlev</span><span class="sxs-lookup"><span data-stu-id="b37b4-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="b37b4-181">`x = y`: Atama</span><span class="sxs-lookup"><span data-stu-id="b37b4-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="b37b4-182">`x op= y`: Bileşik atama; desteklenen işleçler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b37b4-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="b37b4-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="b37b4-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="b37b4-184">`(T x) => y`: Anonim işlevi (lambda ifadesi)</span><span class="sxs-lookup"><span data-stu-id="b37b4-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="b37b4-185">[Önceki](types-and-variables.md)
> [İleri](statements.md)</span><span class="sxs-lookup"><span data-stu-id="b37b4-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
