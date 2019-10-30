---
title: Desen Eşleştirme
description: Verileri mantıksal yapılara göre karşılaştırmak, F# verileri yapısal parçalar halinde çıkarmak veya verilerden bilgi ayıklamak için desenlerin ' de nasıl kullanıldığını öğrenin.
ms.date: 10/27/2019
ms.openlocfilehash: 1acb795cbe5581898ae5e1439098f906a8a16b93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041005"
---
# <a name="pattern-matching"></a><span data-ttu-id="9754a-103">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="9754a-103">Pattern Matching</span></span>

<span data-ttu-id="9754a-104">Desenler, giriş verilerini dönüştürmek için kurallardır.</span><span class="sxs-lookup"><span data-stu-id="9754a-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="9754a-105">Bu F# diller, verileri mantıksal bir yapı veya yapılarla karşılaştırmak, verileri yapısal parçalar halinde çıkarmak veya verileri çeşitli yollarla ayıklamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="9754a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9754a-106">Remarks</span></span>

<span data-ttu-id="9754a-107">Desenler, `match` ifadesi gibi birçok dil yapılarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="9754a-108">`let` bağlamaları, lambda ifadeleri ve `try...with` ifadesiyle ilişkili özel durum işleyicilerde işlevler için bağımsız değişkenleri işlerken kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="9754a-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="9754a-109">Daha fazla bilgi için bkz. [Match ifadeleri](match-expressions.md), [Let bağlamaları](./functions/let-bindings.md), [lambda ifadeleri: `fun` anahtar sözcüğü](./functions/lambda-expressions-the-fun-keyword.md)ve [özel durumlar: `try...with` ifadesi](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="9754a-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="9754a-110">Örneğin, `match` ifadesinde, *Düzen* kanal sembolünü takip eder.</span><span class="sxs-lookup"><span data-stu-id="9754a-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="9754a-111">Her bir model girişi bir şekilde dönüştürmek için bir kural işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="9754a-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="9754a-112">`match` ifadesinde her bir model, giriş verilerinin örüntüle uyumlu olup olmadığını görmek için sırasıyla incelenir.</span><span class="sxs-lookup"><span data-stu-id="9754a-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="9754a-113">Bir eşleşme bulunursa sonuç ifadesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9754a-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="9754a-114">Bir eşleşme bulunmazsa, sonraki model kuralı test edilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="9754a-115">*Koşul* bölümü [eşleşme ifadeleriyle](match-expressions.md)açıklandığında isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9754a-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="9754a-116">Desteklenen desenler aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9754a-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="9754a-117">Çalışma zamanında, giriş, tabloda listelenen sırada aşağıdaki desenlerden her birine karşı test edilir ve desenler yinelemeli olarak, kodunuzda göründükleri gibi ve her satırdaki desenler için soldan sağa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9754a-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="9754a-118">Name</span><span class="sxs-lookup"><span data-stu-id="9754a-118">Name</span></span>|<span data-ttu-id="9754a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9754a-119">Description</span></span>|<span data-ttu-id="9754a-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="9754a-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="9754a-121">Sabit model</span><span class="sxs-lookup"><span data-stu-id="9754a-121">Constant pattern</span></span>|<span data-ttu-id="9754a-122">Herhangi bir sayısal, karakter veya dize sabiti, bir numaralandırma sabiti veya tanımlanmış değişmez değer tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="9754a-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="9754a-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="9754a-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="9754a-124">Tanımlayıcı stili</span><span class="sxs-lookup"><span data-stu-id="9754a-124">Identifier pattern</span></span>|<span data-ttu-id="9754a-125">Ayrılmış birleşimin, özel durum etiketinin veya etkin bir model durumunun Case değeri</span><span class="sxs-lookup"><span data-stu-id="9754a-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="9754a-126">Değişken model</span><span class="sxs-lookup"><span data-stu-id="9754a-126">Variable pattern</span></span>|<span data-ttu-id="9754a-127">*Tanımlayıcısını*</span><span class="sxs-lookup"><span data-stu-id="9754a-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="9754a-128">`as` deseninin</span><span class="sxs-lookup"><span data-stu-id="9754a-128">`as` pattern</span></span>|<span data-ttu-id="9754a-129">*tanımlayıcı* olarak *model*</span><span class="sxs-lookup"><span data-stu-id="9754a-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="9754a-130">VEYA desenli</span><span class="sxs-lookup"><span data-stu-id="9754a-130">OR pattern</span></span>|<span data-ttu-id="9754a-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="9754a-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="9754a-132">VE model</span><span class="sxs-lookup"><span data-stu-id="9754a-132">AND pattern</span></span>|<span data-ttu-id="9754a-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="9754a-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="9754a-134">Dezavantajla</span><span class="sxs-lookup"><span data-stu-id="9754a-134">Cons pattern</span></span>|<span data-ttu-id="9754a-135">*tanımlayıcı* :: *list-Identifier*</span><span class="sxs-lookup"><span data-stu-id="9754a-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="9754a-136">Liste kalıbı</span><span class="sxs-lookup"><span data-stu-id="9754a-136">List pattern</span></span>|<span data-ttu-id="9754a-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="9754a-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="9754a-138">Dizi düzeni</span><span class="sxs-lookup"><span data-stu-id="9754a-138">Array pattern</span></span>|<span data-ttu-id="9754a-139">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="9754a-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="9754a-140">Parantez içine alınmış desenler</span><span class="sxs-lookup"><span data-stu-id="9754a-140">Parenthesized pattern</span></span>|<span data-ttu-id="9754a-141">( *model* )</span><span class="sxs-lookup"><span data-stu-id="9754a-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="9754a-142">Tanımlama grubu düzeni</span><span class="sxs-lookup"><span data-stu-id="9754a-142">Tuple pattern</span></span>|<span data-ttu-id="9754a-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="9754a-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="9754a-144">Kayıt stili</span><span class="sxs-lookup"><span data-stu-id="9754a-144">Record pattern</span></span>|<span data-ttu-id="9754a-145">{ *ıdentifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="9754a-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="9754a-146">Joker karakter stili</span><span class="sxs-lookup"><span data-stu-id="9754a-146">Wildcard pattern</span></span>|<span data-ttu-id="9754a-147">_</span><span class="sxs-lookup"><span data-stu-id="9754a-147">_</span></span>|`_`|
|<span data-ttu-id="9754a-148">Tür ek açıklaması ile birlikte desenler</span><span class="sxs-lookup"><span data-stu-id="9754a-148">Pattern together with type annotation</span></span>|<span data-ttu-id="9754a-149">*model* : *tür*</span><span class="sxs-lookup"><span data-stu-id="9754a-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="9754a-150">Test modelini yazın</span><span class="sxs-lookup"><span data-stu-id="9754a-150">Type test pattern</span></span>|<span data-ttu-id="9754a-151">:?</span><span class="sxs-lookup"><span data-stu-id="9754a-151">:?</span></span> <span data-ttu-id="9754a-152">*tür* [as *Identifier* ]</span><span class="sxs-lookup"><span data-stu-id="9754a-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="9754a-153">Null desenli</span><span class="sxs-lookup"><span data-stu-id="9754a-153">Null pattern</span></span>|<span data-ttu-id="9754a-154">null</span><span class="sxs-lookup"><span data-stu-id="9754a-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="9754a-155">Sabit desenler</span><span class="sxs-lookup"><span data-stu-id="9754a-155">Constant Patterns</span></span>

<span data-ttu-id="9754a-156">Sabit desenler sayısal, karakter ve dize değişmez değerleri, numaralandırma sabitleridir (numaralandırma türü adı dahil).</span><span class="sxs-lookup"><span data-stu-id="9754a-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="9754a-157">Yalnızca sabit desenleri olan bir `match` ifadesi, diğer dillerdeki Case ifadesiyle karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="9754a-158">Giriş değişmez değerle karşılaştırılır ve Değerler eşitse, model eşleşir.</span><span class="sxs-lookup"><span data-stu-id="9754a-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="9754a-159">Sabit değerin türü, girişin türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9754a-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="9754a-160">Aşağıdaki örnek, değişmez değer desenlerinin kullanımını gösterir ve ayrıca bir değişken deseni ve ya da deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="9754a-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="9754a-161">Sabit değer deseninin başka bir örneği, numaralandırma sabitlerine dayanan bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="9754a-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="9754a-162">Sabit Listesi sabitleri kullandığınızda numaralandırma türü adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9754a-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="9754a-163">Tanımlayıcı desenleri</span><span class="sxs-lookup"><span data-stu-id="9754a-163">Identifier Patterns</span></span>

<span data-ttu-id="9754a-164">Desenler, geçerli bir tanımlayıcı oluşturan karakterlerden oluşan bir dizeyse tanımlayıcı formu, düzenin nasıl eşleştirileceği belirler.</span><span class="sxs-lookup"><span data-stu-id="9754a-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="9754a-165">Tanımlayıcı tek bir karakterden uzunsa ve büyük harfli bir karakterle başlıyorsa, derleyici tanımlayıcı düzeniyle bir eşleşme yapmayı dener.</span><span class="sxs-lookup"><span data-stu-id="9754a-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="9754a-166">Bu düzenin tanımlayıcısı, değişmez değer özniteliğiyle, ayırt edici birleşim durumuyla, özel durum tanımlayıcısıyla veya etkin bir model durumuyla işaretlenmiş bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="9754a-167">Eşleşen bir tanımlayıcı bulunamazsa, eşleşme başarısız olur ve sonraki model kuralı, değişken deseninin girişi ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="9754a-168">Ayırt edici bileşim desenleri basit adlandırılmış durumlar olabilir veya bir değer ya da birden çok değer içeren bir tanımlama grubu olabilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="9754a-169">Bir değer varsa, değer için bir tanımlayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9754a-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="9754a-170">Bir tanımlama grubu söz konusu olduğunda, bir veya daha fazla adlandırılmış UNION alanı için, kayıt düzeninin her öğesi için tanımlayıcı veya bir alan adı olan bir tanımlayıcı içeren bir tanımlama grubu düzeni sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9754a-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="9754a-171">Örnekler için bu bölümdeki kod örneklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="9754a-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="9754a-172">`option` türü, iki durum, `Some` ve `None`olan ayırt edici bir birleşimdir.</span><span class="sxs-lookup"><span data-stu-id="9754a-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="9754a-173">Bir durumda (`Some`) bir değer vardır, ancak diğeri (`None`) yalnızca adlandırılmış bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="9754a-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="9754a-174">Bu nedenle, `Some` `Some` durumuyla ilişkili değer için bir değişkene sahip olması gerekir, ancak `None` kendi kendine gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="9754a-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="9754a-175">Aşağıdaki kodda `var1` değişkenine, `Some` durumu ile eşleştirilirken elde edilen değer verilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="9754a-176">Aşağıdaki örnekte, `PersonName` ayırt edici birleşim, olası ad biçimlerini temsil eden dizelerin ve karakterlerin bir karışımını içerir.</span><span class="sxs-lookup"><span data-stu-id="9754a-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="9754a-177">Ayırt edici birleşimin durumları `FirstOnly`, `LastOnly`ve `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="9754a-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="9754a-178">Adlandırılmış alanları olan ayrılmış birleşimler için, adlandırılmış bir alanın değerini çıkarmak için eşittir işaretini (=) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9754a-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="9754a-179">Örneğin, aşağıdaki gibi bir bildirime sahip ayrılmış bir birleşim düşünün.</span><span class="sxs-lookup"><span data-stu-id="9754a-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="9754a-180">Bir model eşleştirme ifadesinde adlandırılmış alanları aşağıdaki gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9754a-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="9754a-181">Adlandırılmış alanın kullanımı isteğe bağlıdır, bu nedenle önceki örnekte hem `Circle(r)` hem de `Circle(radius = r)` aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9754a-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="9754a-182">Birden çok alan belirttiğinizde, noktalı virgül kullanın (;) ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="9754a-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="9754a-183">Etkin desenler, daha karmaşık özel desen eşleştirmeyi tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9754a-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="9754a-184">Etkin desenler hakkında daha fazla bilgi için bkz. [Etkin desenler](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="9754a-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="9754a-185">Tanımlayıcının özel durum olduğu durum, özel durum işleyicileri bağlamında model eşleştirme içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="9754a-186">Özel durum işlemede model eşleştirme hakkında daha fazla bilgi için bkz. [özel durumlar: `try...with` ifadesi](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="9754a-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="9754a-187">Değişken desenleri</span><span class="sxs-lookup"><span data-stu-id="9754a-187">Variable Patterns</span></span>

<span data-ttu-id="9754a-188">Değişken stili, eşlenen değeri bir değişken adıyla atar ve bu daha sonra `->` simgenin sağında yürütme ifadesinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="9754a-189">Bir değişken deseni her türlü girişle eşleşir, ancak değişken desenleri genellikle diğer desenlerde görünür, bu nedenle, değişkenlere ve dizilere gibi daha karmaşık yapıların bağımsız değişkenlere çıkarılması mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="9754a-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="9754a-190">Aşağıdaki örnek, bir demet deseninin içindeki değişken bir düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="9754a-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="9754a-191">as model</span><span class="sxs-lookup"><span data-stu-id="9754a-191">as Pattern</span></span>

<span data-ttu-id="9754a-192">`as` deseninin eklendiği bir `as` yan tümcesi olan bir örüntü.</span><span class="sxs-lookup"><span data-stu-id="9754a-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="9754a-193">`as` yan tümcesi, eşleşen değeri bir `match` ifadesinin yürütme ifadesinde kullanılabilecek bir ada bağlar veya bu düzenin bir `let` bağlamasında kullanıldığı durumda, ad yerel kapsama bir bağlama olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="9754a-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="9754a-194">Aşağıdaki örnek bir `as` modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9754a-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="9754a-195">VEYA desenli</span><span class="sxs-lookup"><span data-stu-id="9754a-195">OR Pattern</span></span>

<span data-ttu-id="9754a-196">OR deseni, giriş verileri birden çok desenle eşleşiyorsa ve sonuç olarak aynı kodu yürütmek istiyorsanız kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="9754a-197">YA da deseninin her iki tarafının türleri uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9754a-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="9754a-198">Aşağıdaki örnek, veya modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9754a-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="9754a-199">VE model</span><span class="sxs-lookup"><span data-stu-id="9754a-199">AND Pattern</span></span>

<span data-ttu-id="9754a-200">VE deseni, girişin iki desenle eşleşmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9754a-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="9754a-201">VE deseninin her iki tarafının türleri uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9754a-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="9754a-202">Aşağıdaki örnek, bu konunun ilerleyen kısımlarında yer [kayıt düzeni](https://msdn.microsoft.com/library/#tuple) bölümünde gösterilen `detectZeroTuple` gibidir, ancak burada `var1` ve `var2` her IKISI de ve düzeni kullanılarak değerler olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="9754a-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="9754a-203">Dezavantajla</span><span class="sxs-lookup"><span data-stu-id="9754a-203">Cons Pattern</span></span>

<span data-ttu-id="9754a-204">Cons stili, bir listeyi ilk öğe, *baş*ve geri kalan öğeleri içeren bir liste, *tail*ve bir liste için bir liste oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="9754a-205">Liste kalıbı</span><span class="sxs-lookup"><span data-stu-id="9754a-205">List Pattern</span></span>

<span data-ttu-id="9754a-206">Liste deseninin, listelerin bir dizi öğe halinde çıkarılması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9754a-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="9754a-207">Liste deseninin kendisi yalnızca belirli sayıdaki öğelerin listeleriyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="9754a-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="9754a-208">Dizi düzeni</span><span class="sxs-lookup"><span data-stu-id="9754a-208">Array Pattern</span></span>

<span data-ttu-id="9754a-209">Dizi düzeni liste düzenine benzer ve belirli uzunluktaki dizileri ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="9754a-210">Parantez içine alınmış desenler</span><span class="sxs-lookup"><span data-stu-id="9754a-210">Parenthesized Pattern</span></span>

<span data-ttu-id="9754a-211">Parantezler, istenen ilişkilendirilebilirliği elde etmek için desenlerin etrafında gruplandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="9754a-212">Aşağıdaki örnekte, parantez ve bir dezavantajla arasındaki ilişkilendirilebilirlik denetlemek için parantezler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="9754a-213">Tanımlama grubu düzeni</span><span class="sxs-lookup"><span data-stu-id="9754a-213">Tuple Pattern</span></span>

<span data-ttu-id="9754a-214">Tanımlama grubu düzeni, kayıt düzeni formundaki giriş ile eşleşir ve kayıt düzeninin her bir konum için model eşleme değişkenlerini kullanarak kendi bileşen öğelerine parçalanmak üzere etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="9754a-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="9754a-215">Aşağıdaki örnek demet desenini gösterir ve aynı zamanda değişmez desenleri, değişken desenleri ve joker karakter desenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9754a-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="9754a-216">Kayıt stili</span><span class="sxs-lookup"><span data-stu-id="9754a-216">Record Pattern</span></span>

<span data-ttu-id="9754a-217">Kayıt stili, alanların değerlerini ayıklamak için kayıt oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="9754a-218">Düzenin kaydın tüm alanlarına başvurması gerekmez; Atlanan tüm alanlar yalnızca eşleştirmeye katılmaz ve ayıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="9754a-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="9754a-219">Joker karakter stili</span><span class="sxs-lookup"><span data-stu-id="9754a-219">Wildcard Pattern</span></span>

<span data-ttu-id="9754a-220">Joker karakter stili, alt çizgi (`_`) karakteriyle temsil edilir ve tıpkı değişken düzeniyle benzer şekilde, girişin bir değişkene atanması yerine atılmasının dışında herhangi bir girişle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="9754a-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="9754a-221">Joker karakter deseni, genellikle `->` simgenin sağında yer alan ifadede gerekli olmayan değerler için yer tutucu olarak diğer desenlerin içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="9754a-222">Joker karakter deseni, eşleşmeyen herhangi bir girişi eşleştirmek için bir desen listesinin sonunda da sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="9754a-223">Bu konudaki çok sayıda kod örneğinde joker karakter deseninin gösterildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9754a-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="9754a-224">Bir örnek için yukarıdaki koda bakın.</span><span class="sxs-lookup"><span data-stu-id="9754a-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="9754a-225">Tür ek açıklamalarına sahip desenler</span><span class="sxs-lookup"><span data-stu-id="9754a-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="9754a-226">Desenlerin tür ek açıklamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-226">Patterns can have type annotations.</span></span> <span data-ttu-id="9754a-227">Bunlar diğer tür ek açıklamaları ve diğer tür ek açıklamaları gibi kılavuz çıkarımı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="9754a-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="9754a-228">Desenlerdeki tür ek açıklamaları etrafında parantezler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9754a-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="9754a-229">Aşağıdaki kod, tür ek açıklamasına sahip bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="9754a-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="9754a-230">Test modelini yazın</span><span class="sxs-lookup"><span data-stu-id="9754a-230">Type Test Pattern</span></span>

<span data-ttu-id="9754a-231">Tür Test deseninin girişi bir türle eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="9754a-232">Giriş türü, düzende belirtilen tür ile bir eşleşmedir (veya türetilmiş bir tür), eşleşme başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="9754a-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="9754a-233">Aşağıdaki örnek, tür testi modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9754a-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

<span data-ttu-id="9754a-234">Yalnızca bir tanımlayıcının belirli bir türetilmiş türde olup olmadığını kontrol ediyorsanız, aşağıdaki örnekte gösterildiği gibi, deseninin `as identifier` bir bölümüne gerek kalmaz:</span><span class="sxs-lookup"><span data-stu-id="9754a-234">If you're only checking if an identifier is of a particular derived type, you don't need the `as identifier` part of the pattern, as shown in the following example:</span></span>

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a><span data-ttu-id="9754a-235">Null desenli</span><span class="sxs-lookup"><span data-stu-id="9754a-235">Null Pattern</span></span>

<span data-ttu-id="9754a-236">Null değer, null değere izin veren türlerle çalışırken görünebilen null değeriyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="9754a-236">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="9754a-237">.NET Framework kodla birlikte çalışırken genellikle null desenler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9754a-237">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="9754a-238">Örneğin, bir .NET API 'nin dönüş değeri bir `match` ifadesi girişi olabilir.</span><span class="sxs-lookup"><span data-stu-id="9754a-238">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="9754a-239">Program akışını, dönüş değerinin null ve ayrıca döndürülen değerin diğer özelliklerine göre kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9754a-239">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="9754a-240">Null değerlerin programınızın geri kalanına yayılmasını engellemek için null kalıbı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9754a-240">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="9754a-241">Aşağıdaki örnek, null ve değişken düzenlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9754a-241">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="9754a-242">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9754a-242">See also</span></span>

- [<span data-ttu-id="9754a-243">Eşleşme İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9754a-243">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="9754a-244">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="9754a-244">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="9754a-245">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9754a-245">F# Language Reference</span></span>](index.md)
