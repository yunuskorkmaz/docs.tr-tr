---
title: C#İfadeleri - Turu C# dil
description: ifadeleri ve işlenenleri işleçleri olan yapı taşları C# dil
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4ffe947a4cb8c36a5925a4b3846486e44a9d8ec4
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480761"
---
# <a name="expressions"></a><span data-ttu-id="ff156-103">İfadeler</span><span class="sxs-lookup"><span data-stu-id="ff156-103">Expressions</span></span>

<span data-ttu-id="ff156-104">*İfadeleri* oluşturulan *işlenenler* ve *işleçleri*.</span><span class="sxs-lookup"><span data-stu-id="ff156-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="ff156-105">İfade işleçleri işlenenlere uygulamak için hangi işlemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff156-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="ff156-106">İşleçler örnekler `+`, `-`, `*`, `/`, ve `new`.</span><span class="sxs-lookup"><span data-stu-id="ff156-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="ff156-107">Değişmez değerler, alanlar, yerel değişkenleri ve ifadeleri işlenenler örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="ff156-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="ff156-108">Bir ifade birden çok işleç içeren *öncelik* işleçleri tek tek işleçler değerlendirilme sırası denetler.</span><span class="sxs-lookup"><span data-stu-id="ff156-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="ff156-109">Örneğin, ifade `x + y * z` değerlendirmesinde `x + (y * z)` çünkü `*` işleci daha yüksek önceliğe sahip `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="ff156-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="ff156-110">Bir işlenen aynı önceliğe sahip iki işleç arasında gerçekleştiğinde *ilişkilendirilebilirliği* operatörleri işlemleri gerçekleştirilir sırasını denetler:</span><span class="sxs-lookup"><span data-stu-id="ff156-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="ff156-111">Atama işleçleri hariç tüm ikili işleçler şunlardır *ilişkilendirilebilir*, yani işlemler soldan sağa doğru gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ff156-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="ff156-112">Örneğin, `x + y + z` değerlendirmesinde `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="ff156-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="ff156-113">Atama işleçleri ve koşullu işleç (`?:`) olan *sağla ilişkilendirilebilir*, sağdan sola işlemler gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ff156-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="ff156-114">Örneğin, `x = y = z` değerlendirmesinde `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="ff156-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="ff156-115">Öncelik ve ilişkisellik parantez kullanılarak denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ff156-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="ff156-116">Örneğin, `x + y * z` ilk çarpar `y` tarafından `z` ve ardından sonuca ekler `x`, ancak `(x + y) * z` ilk ekler `x` ve `y` ve sonucu çarpan `z`.</span><span class="sxs-lookup"><span data-stu-id="ff156-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="ff156-117">Çoğu işleçleri olabilir *aşırı*.</span><span class="sxs-lookup"><span data-stu-id="ff156-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="ff156-118">İşleç aşırı yüklemesi, aşağıdakilerden birini veya her iki işlenen kullanıcı tanımlı sınıf veya yapı türü olduğu işlemlerinde belirtilmesi için kullanıcı tanımlı işleç uygulamalarına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ff156-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="ff156-119">Aşağıdaki özetler C#'s işleçlerini, en düşük yüksekten öncelik sırasına işleci kategorileri listeleme.</span><span class="sxs-lookup"><span data-stu-id="ff156-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="ff156-120">Aynı kategoride işleçleri eşit önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ff156-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="ff156-121">Her kategori altında bu ifade türünün açıklaması ile birlikte bu kategorideki ifadeleri listesidir.</span><span class="sxs-lookup"><span data-stu-id="ff156-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="ff156-122">Birincil</span><span class="sxs-lookup"><span data-stu-id="ff156-122">Primary</span></span>
  - `x.m`<span data-ttu-id="ff156-123">: Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="ff156-123">: Member access</span></span>
  - `x(...)`<span data-ttu-id="ff156-124">: Yöntem ve temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="ff156-124">: Method and delegate invocation</span></span>
  - `x[...]`<span data-ttu-id="ff156-125">: Dizi ve dizinleyici erişimi</span><span class="sxs-lookup"><span data-stu-id="ff156-125">: Array and indexer access</span></span>
  - `x++`<span data-ttu-id="ff156-126">: Artırım sonrası</span><span class="sxs-lookup"><span data-stu-id="ff156-126">: Post-increment</span></span>
  - `x--`<span data-ttu-id="ff156-127">: Azaltım sonrası</span><span class="sxs-lookup"><span data-stu-id="ff156-127">: Post-decrement</span></span>
  - `new T(...)`<span data-ttu-id="ff156-128">: Nesne ve temsilci oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff156-128">: Object and delegate creation</span></span>
  - `new T(...){...}`<span data-ttu-id="ff156-129">: Başlatıcı ile nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff156-129">: Object creation with initializer</span></span>
  - `new {...}`<span data-ttu-id="ff156-130">:  Anonim nesne Başlatıcı</span><span class="sxs-lookup"><span data-stu-id="ff156-130">:  Anonymous object initializer</span></span>
  - `new T[...]`<span data-ttu-id="ff156-131">: Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff156-131">: Array creation</span></span>
  - `typeof(T)`<span data-ttu-id="ff156-132">: Elde <xref:System.Type> nesnesi</span><span class="sxs-lookup"><span data-stu-id="ff156-132">: Obtain <xref:System.Type> object for</span></span> `T`
  - `checked(x)`<span data-ttu-id="ff156-133">: İşaretli bağlamında ifade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ff156-133">: Evaluate expression in checked context</span></span>
  - `unchecked(x)`<span data-ttu-id="ff156-134">: İşaretlenmemiş bağlamında ifade değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ff156-134">: Evaluate expression in unchecked context</span></span>
  - `default(T)`<span data-ttu-id="ff156-135">: Türünün varsayılan değerini alın</span><span class="sxs-lookup"><span data-stu-id="ff156-135">: Obtain default value of type</span></span> `T`
  - `delegate {...}`<span data-ttu-id="ff156-136">: Anonim işlevi (anonim yöntemi)</span><span class="sxs-lookup"><span data-stu-id="ff156-136">: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="ff156-137">Birli</span><span class="sxs-lookup"><span data-stu-id="ff156-137">Unary</span></span>
  - `+x`<span data-ttu-id="ff156-138">: Kimlik</span><span class="sxs-lookup"><span data-stu-id="ff156-138">: Identity</span></span>
  - `-x`<span data-ttu-id="ff156-139">: Olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="ff156-139">: Negation</span></span>
  - `!x`<span data-ttu-id="ff156-140">: Mantıksal olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="ff156-140">: Logical negation</span></span>
  - `~x`<span data-ttu-id="ff156-141">: Bitwise olumsuzlama</span><span class="sxs-lookup"><span data-stu-id="ff156-141">: Bitwise negation</span></span>
  - `++x`<span data-ttu-id="ff156-142">: Artırım öncesi</span><span class="sxs-lookup"><span data-stu-id="ff156-142">: Pre-increment</span></span>
  - `--x`<span data-ttu-id="ff156-143">: Azaltım öncesi</span><span class="sxs-lookup"><span data-stu-id="ff156-143">: Pre-decrement</span></span>
  - `(T)x`<span data-ttu-id="ff156-144">: Açıkça dönüştürmek `x` yazmak için</span><span class="sxs-lookup"><span data-stu-id="ff156-144">: Explicitly convert `x` to type</span></span> `T`
  - `await x`<span data-ttu-id="ff156-145">: Zaman uyumsuz olarak bekleyin `x` tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="ff156-145">: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="ff156-146">Çarpma</span><span class="sxs-lookup"><span data-stu-id="ff156-146">Multiplicative</span></span>
  - `x * y`<span data-ttu-id="ff156-147">: Çarpma</span><span class="sxs-lookup"><span data-stu-id="ff156-147">: Multiplication</span></span>
  - `x / y`<span data-ttu-id="ff156-148">: Bölme</span><span class="sxs-lookup"><span data-stu-id="ff156-148">: Division</span></span>
  - `x % y`<span data-ttu-id="ff156-149">: Kalan</span><span class="sxs-lookup"><span data-stu-id="ff156-149">: Remainder</span></span>
* <span data-ttu-id="ff156-150">Eklenebilir</span><span class="sxs-lookup"><span data-stu-id="ff156-150">Additive</span></span>
  - `x + y`<span data-ttu-id="ff156-151">: Toplama, dize bitiştirme, temsilci birleşimi</span><span class="sxs-lookup"><span data-stu-id="ff156-151">: Addition, string concatenation, delegate combination</span></span>
  - `x – y`<span data-ttu-id="ff156-152">: Çıkarma, temsilci kaldırma</span><span class="sxs-lookup"><span data-stu-id="ff156-152">: Subtraction, delegate removal</span></span>
* <span data-ttu-id="ff156-153">Shift</span><span class="sxs-lookup"><span data-stu-id="ff156-153">Shift</span></span>
  - `x << y`<span data-ttu-id="ff156-154">: Sola kaydırma</span><span class="sxs-lookup"><span data-stu-id="ff156-154">: Shift left</span></span>
  - `x >> y`<span data-ttu-id="ff156-155">: Sağa kaydırma</span><span class="sxs-lookup"><span data-stu-id="ff156-155">: Shift right</span></span>
* <span data-ttu-id="ff156-156">İlişkisel ve tür testi</span><span class="sxs-lookup"><span data-stu-id="ff156-156">Relational and type testing</span></span>
  - `x < y`<span data-ttu-id="ff156-157">: Küçüktür</span><span class="sxs-lookup"><span data-stu-id="ff156-157">: Less than</span></span>
  - `x > y`<span data-ttu-id="ff156-158">: Büyüktür</span><span class="sxs-lookup"><span data-stu-id="ff156-158">: Greater than</span></span>
  - `x <= y`<span data-ttu-id="ff156-159">: Küçük veya eşittir</span><span class="sxs-lookup"><span data-stu-id="ff156-159">: Less than or equal</span></span>
  - `x >= y`<span data-ttu-id="ff156-160">: Büyük veya eşittir</span><span class="sxs-lookup"><span data-stu-id="ff156-160">: Greater than or equal</span></span>
  - `x is T`<span data-ttu-id="ff156-161">: Dönüş `true` varsa `x` olduğu bir `T`, `false` Aksi takdirde</span><span class="sxs-lookup"><span data-stu-id="ff156-161">: Return `true` if `x` is a `T`, `false` otherwise</span></span>
  - `x as T`<span data-ttu-id="ff156-162">: Dönüş `x` olarak yazılan `T`, veya `null` varsa `x` değil bir</span><span class="sxs-lookup"><span data-stu-id="ff156-162">: Return `x` typed as `T`, or `null` if `x` is not a</span></span> `T`
* <span data-ttu-id="ff156-163">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="ff156-163">Equality</span></span>
  - `x == y`<span data-ttu-id="ff156-164">: Eşittir</span><span class="sxs-lookup"><span data-stu-id="ff156-164">: Equal</span></span>
  - `x != y`<span data-ttu-id="ff156-165">: Eşit değildir</span><span class="sxs-lookup"><span data-stu-id="ff156-165">: Not equal</span></span>
* <span data-ttu-id="ff156-166">Mantıksal VE</span><span class="sxs-lookup"><span data-stu-id="ff156-166">Logical AND</span></span>
  - `x & y`<span data-ttu-id="ff156-167">: Tamsayı bitwise ve, boolean mantıksal ve</span><span class="sxs-lookup"><span data-stu-id="ff156-167">: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="ff156-168">Mantıksal XOR</span><span class="sxs-lookup"><span data-stu-id="ff156-168">Logical XOR</span></span>
  - `x ^ y`<span data-ttu-id="ff156-169">: Tamsayı bitwise XOR, Boolean mantıksal XOR</span><span class="sxs-lookup"><span data-stu-id="ff156-169">: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="ff156-170">Mantıksal VEYA</span><span class="sxs-lookup"><span data-stu-id="ff156-170">Logical OR</span></span>
  - `x | y`<span data-ttu-id="ff156-171">: Tamsayı bitwise VEYA, boolean mantıksal VEYA</span><span class="sxs-lookup"><span data-stu-id="ff156-171">: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="ff156-172">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="ff156-172">Conditional AND</span></span>
  - `x && y`<span data-ttu-id="ff156-173">: Değerlendirilen `y` yalnızca `x` değil</span><span class="sxs-lookup"><span data-stu-id="ff156-173">: Evaluates `y` only if `x` is not</span></span> `false`
* <span data-ttu-id="ff156-174">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="ff156-174">Conditional OR</span></span>
  - `x || y`<span data-ttu-id="ff156-175">: Değerlendirilen `y` yalnızca `x` değil</span><span class="sxs-lookup"><span data-stu-id="ff156-175">: Evaluates `y` only if `x` is not</span></span> `true`
* <span data-ttu-id="ff156-176">Null birleşim</span><span class="sxs-lookup"><span data-stu-id="ff156-176">Null coalescing</span></span>
  - `x ?? y`<span data-ttu-id="ff156-177">: Değerlendiren `y` varsa `x` için null `x` Aksi takdirde</span><span class="sxs-lookup"><span data-stu-id="ff156-177">: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="ff156-178">Koşullu</span><span class="sxs-lookup"><span data-stu-id="ff156-178">Conditional</span></span>
  - `x ? y : z`<span data-ttu-id="ff156-179">: Değerlendirir `y` varsa `x` olduğu `true`, `z` varsa `x` olduğu</span><span class="sxs-lookup"><span data-stu-id="ff156-179">: Evaluates `y` if `x` is `true`, `z` if `x` is</span></span> `false`
* <span data-ttu-id="ff156-180">Atama ve anonim işlev</span><span class="sxs-lookup"><span data-stu-id="ff156-180">Assignment or anonymous function</span></span>
  - `x = y`<span data-ttu-id="ff156-181">: Atama</span><span class="sxs-lookup"><span data-stu-id="ff156-181">: Assignment</span></span>
  - `x op= y`<span data-ttu-id="ff156-182">: Bileşik atama; desteklenen işleçler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ff156-182">: Compound assignment; supported operators are</span></span>
    - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
  - `(T x) => y`<span data-ttu-id="ff156-183">: Anonim işlevi (lambda ifadesi)</span><span class="sxs-lookup"><span data-stu-id="ff156-183">: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="ff156-184">[Önceki](types-and-variables.md)
> [İleri](statements.md)</span><span class="sxs-lookup"><span data-stu-id="ff156-184">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
