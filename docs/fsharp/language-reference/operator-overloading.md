---
title: İşleç Aşırı Yüklemesi (F#)
description: 'Aritmetik işleçler bir sınıf veya kayıt türü ve F # içinde genel düzeyde aşırı yüklemeyi öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: fc9b7311aa746fd758930365972a187ffdfff0d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="operator-overloading"></a><span data-ttu-id="bbbb0-103">İşleç Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="bbbb0-103">Operator Overloading</span></span>

<span data-ttu-id="bbbb0-104">Bu konuda, bir sınıf ya da kayıt türü ve genel düzeyde aritmetik işleçler aşırı yüklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>


## <a name="syntax"></a><span data-ttu-id="bbbb0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbbb0-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="bbbb0-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbbb0-106">Remarks</span></span>
<span data-ttu-id="bbbb0-107">Önceki sözdiziminde *işleç simgesi* biri `+`, `-`, `*`, `/`, `=`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="bbbb0-108">*Parametre listesi* işlenenler göründükleri normal sözdiziminde işleç için sıra belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="bbbb0-109">*Yöntem gövdesi* sonuç değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="bbbb0-110">İşleç aşırı yüklemeleri işleçleri için statik olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="bbbb0-111">İşleci birli işleçler için gibi aşırı yüklemeler `+` ve `-`, bir tilde kullanmanız gerekir (`~`) içinde *işleç simgesi* işleci birli işleç ve ikili işleç değil de gösterildiği gibi olduğunu göstermek için Aşağıdaki bildirimi.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="bbbb0-112">Aşağıdaki kod yalnızca iki işleç olan bir vektör sınıfı gösterir tekli eksi, diğeri skaler tarafından çarpma için için.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="bbbb0-113">İşleç vektör ve skaler görünme sırasını bağımsız olarak çalışması gerekir çünkü örnekte, iki aşırı skaler çarpma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="bbbb0-114">Yeni işleçleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="bbbb0-114">Creating New Operators</span></span>
<span data-ttu-id="bbbb0-115">Tüm standart işleçleri aşırı yüklenebilir, ancak belirli karakter dizileri dışında yeni işleçleri de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="bbbb0-116">İşleç karakterler izin `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, ve `~`.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="bbbb0-117">`~` Karakter işleci birli yapma özel bir anlamı yoktur ve işleci karakter dizisinin bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="bbbb0-118">Tüm işleçleri birli yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="bbbb0-119">Kullandığınız tam karakter dizisi bağlı olarak, belirli bir öncelik ve birleşim operatörünüze sahip olur.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="bbbb0-120">Birleşim sağdan sola veya sağa ya da bırakılabilir ve parantezler olmadan sırası aynı öncelik düzeyine operatörleri görünür olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="bbbb0-121">İşleç karakter `.` Örneğin, gibiişleçlerinoluşturmakaynıöncelikvebirleşimsıradançarpmaolaraksahipçarpmakendisürümünütanımlamakistiyorsanız,böyleceönceliği,etkilemez `.*`.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="bbbb0-122">Yalnızca işleçleri `?` ve `?<-` ile başlayabilir `?`.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="bbbb0-123">Tüm işleçleri önceliğini F #'ta gösteren bir tablo bulunabilir [simge ve işleç başvurusu](symbol-and-operator-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="bbbb0-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](symbol-and-operator-reference/index.md).</span></span>


## <a name="overloaded-operator-names"></a><span data-ttu-id="bbbb0-124">Aşırı yüklenmiş işleci adları</span><span class="sxs-lookup"><span data-stu-id="bbbb0-124">Overloaded Operator Names</span></span>
<span data-ttu-id="bbbb0-125">F # derleyici işleci ifade derlediğinde işleç için derleyici tarafından üretilen bir ada sahip bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="bbbb0-126">Bu yöntem için Microsoft Ara dilde (MSIL) ve yansıma ve IntelliSense görünen addır.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="bbbb0-127">Normalde bu adları F # kodunda kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="bbbb0-128">Aşağıdaki tablo standart işleçler gösterir ve karşılık gelen adları oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-128">The following table shows the standard operators and their corresponding generated names.</span></span>



|<span data-ttu-id="bbbb0-129">İşleç</span><span class="sxs-lookup"><span data-stu-id="bbbb0-129">Operator</span></span>|<span data-ttu-id="bbbb0-130">Oluşturulan adı</span><span class="sxs-lookup"><span data-stu-id="bbbb0-130">Generated name</span></span>|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|
<span data-ttu-id="bbbb0-131">Burada listelenmeyen işleci karakterden diğer bileşimlerini işletmenler olarak kullanılabilir ve aşağıdaki tablodan tek tek karakter adları birleştirerek oluşur adlara sahip.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-131">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="bbbb0-132">Örneğin, +!</span><span class="sxs-lookup"><span data-stu-id="bbbb0-132">For example, +!</span></span> <span data-ttu-id="bbbb0-133">hale `op_PlusBang`.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-133">becomes `op_PlusBang`.</span></span>



|<span data-ttu-id="bbbb0-134">İşleç karakter</span><span class="sxs-lookup"><span data-stu-id="bbbb0-134">Operator character</span></span>|<span data-ttu-id="bbbb0-135">Ad</span><span class="sxs-lookup"><span data-stu-id="bbbb0-135">Name</span></span>|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="bbbb0-136">Önek ve iç işleçleri</span><span class="sxs-lookup"><span data-stu-id="bbbb0-136">Prefix and Infix Operators</span></span>
<span data-ttu-id="bbbb0-137">*Önek* işleçleri işleneni veya benzer bir işlev işlenenler önünde yerleştirilmesi beklenir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-137">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="bbbb0-138">*İnfix* işleçleri arasında iki işlenen yerleştirilmesi beklenir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-138">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="bbbb0-139">Yalnızca belirli işleçleri önek operatörleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-139">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="bbbb0-140">Bazı işleçler her önek operatörleri, diğerleri iç veya önek olabilir ve geri kalan her zaman işleçleri infix.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-140">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="bbbb0-141">İle başlayan işleçleri `!`, dışında `!=`and işleci `~`, veya yinelenen dizilerini`~`, her zaman önek işleçler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-141">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="bbbb0-142">İşleçler `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, ve `%%` önek işleçleri veya işleçleri infix olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-142">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="bbbb0-143">Bu işleçlere önek sürümü ekleyerek iç sürümünden ayırt bir `~` çok tanımlandığında bir önek işleci başındaki.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-143">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="bbbb0-144">`~` Yalnızca tanımlandığında işleci kullandığınızda kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-144">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="bbbb0-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbbb0-145">Example</span></span>

<span data-ttu-id="bbbb0-146">Aşağıdaki kod bir kesir türü uygulamak için işleç aşırı yüklemesi kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-146">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="bbbb0-147">Kesir bir pay ve bir paydası tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-147">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="bbbb0-148">İşlev `hcf` kesirler azaltmak için kullanılan en yüksek ortak çarpanını belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-148">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="bbbb0-149">**Çıktı:**</span><span class="sxs-lookup"><span data-stu-id="bbbb0-149">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="bbbb0-150">Genel düzeyde işleçleri</span><span class="sxs-lookup"><span data-stu-id="bbbb0-150">Operators at the Global Level</span></span>
<span data-ttu-id="bbbb0-151">Genel düzeyde işleçleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-151">You can also define operators at the global level.</span></span> <span data-ttu-id="bbbb0-152">Aşağıdaki kod bir işleç tanımlar `+?`.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-152">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="bbbb0-153">Yukarıdaki kod çıkışıdır `12`.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-153">The output of the above code is `12`.</span></span>

<span data-ttu-id="bbbb0-154">Kapsam kuralları F # için yeni tanımlanan işleçleri yerleşik işleçleri önceliklidir dikte çünkü bu şekilde normal aritmetik işleçler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-154">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="bbbb0-155">Anahtar sözcüğü `inline` çoğunlukla genellikle en iyi arama koda tümleşik küçük işlevlerdir genel işleçleri ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-155">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="bbbb0-156">Yapma işleci işlevler satır içi bunları statik olarak çözümlenmiş genel kod üretmek için statik olarak çözümlenmiş tür parametreleri ile çalışmak etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-156">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="bbbb0-157">Daha fazla bilgi için bkz: [satır içi işlevler](functions/inline-functions.md) ve [statik olarak çözümlenmiş tür parametreleri](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="bbbb0-157">For more information, see [Inline Functions](functions/inline-functions.md) and [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bbbb0-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbbb0-158">See Also</span></span>
[<span data-ttu-id="bbbb0-159">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bbbb0-159">Members</span></span>](members/index.md)
