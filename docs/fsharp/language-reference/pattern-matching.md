---
title: Desen Eşleştirme
description: 'Verileri mantıksal yapılara göre karşılaştırmak, verileri yapısal parçalar halinde çıkarmak veya verilerden bilgi ayıklamak için F # içinde desenlerin nasıl kullanıldığını öğrenin.'
ms.date: 11/12/2020
ms.openlocfilehash: e167712b082b7f587e41a78edcaf0a0db9c7294b
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687811"
---
# <a name="pattern-matching"></a><span data-ttu-id="23031-103">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="23031-103">Pattern Matching</span></span>

<span data-ttu-id="23031-104">Desenler, giriş verilerini dönüştürmek için kurallardır.</span><span class="sxs-lookup"><span data-stu-id="23031-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="23031-105">Verileri bir mantıksal yapı veya yapılarla karşılaştırmak, verileri yapısal parçalar halinde çıkarmak veya verileri çeşitli yollarla ayıklamak için F # dilinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="23031-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23031-106">Remarks</span></span>

<span data-ttu-id="23031-107">Desenler, ifadesi gibi birçok dil yapılarında kullanılır `match` .</span><span class="sxs-lookup"><span data-stu-id="23031-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="23031-108">`let`Bağlamalar, lambda ifadeleri ve ifadeyle ilişkili özel durum işleyicilerde işlevler için bağımsız değişkenleri işlerken kullanılırlar `try...with` .</span><span class="sxs-lookup"><span data-stu-id="23031-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="23031-109">Daha fazla bilgi için bkz. [Match ifadeleri](match-expressions.md), [Let bağlamaları](./functions/let-bindings.md), [lambda Ifadeleri: `fun` anahtar sözcüğü](./functions/lambda-expressions-the-fun-keyword.md)ve [özel durumlar: `try...with` ifade](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="23031-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="23031-110">Örneğin, `match` ifadesinde, *Düzen* kanal sembolünü izleyen şeydir.</span><span class="sxs-lookup"><span data-stu-id="23031-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="23031-111">Her bir model girişi bir şekilde dönüştürmek için bir kural işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="23031-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="23031-112">`match`İfadesinde, her bir model, giriş verilerinin örüntüle uyumlu olup olmadığını görmek için sırasıyla incelenir.</span><span class="sxs-lookup"><span data-stu-id="23031-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="23031-113">Bir eşleşme bulunursa sonuç ifadesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="23031-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="23031-114">Bir eşleşme bulunmazsa, sonraki model kuralı test edilir.</span><span class="sxs-lookup"><span data-stu-id="23031-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="23031-115">*Koşul* bölümü [eşleşme ifadeleriyle](match-expressions.md)açıklandığında isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="23031-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="23031-116">Desteklenen desenler aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="23031-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="23031-117">Çalışma zamanında, giriş, tabloda listelenen sırada aşağıdaki desenlerden her birine karşı test edilir ve desenler yinelemeli olarak, kodunuzda göründükleri gibi ve her satırdaki desenler için soldan sağa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="23031-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="23031-118">Ad</span><span class="sxs-lookup"><span data-stu-id="23031-118">Name</span></span>|<span data-ttu-id="23031-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23031-119">Description</span></span>|<span data-ttu-id="23031-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="23031-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="23031-121">Sabit model</span><span class="sxs-lookup"><span data-stu-id="23031-121">Constant pattern</span></span>|<span data-ttu-id="23031-122">Herhangi bir sayısal, karakter veya dize sabiti, bir numaralandırma sabiti veya tanımlanmış değişmez değer tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="23031-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="23031-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="23031-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="23031-124">Tanımlayıcı stili</span><span class="sxs-lookup"><span data-stu-id="23031-124">Identifier pattern</span></span>|<span data-ttu-id="23031-125">Ayrılmış birleşimin, özel durum etiketinin veya etkin bir model durumunun Case değeri</span><span class="sxs-lookup"><span data-stu-id="23031-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="23031-126">Değişken model</span><span class="sxs-lookup"><span data-stu-id="23031-126">Variable pattern</span></span>|<span data-ttu-id="23031-127">*Tanımlayıcısını*</span><span class="sxs-lookup"><span data-stu-id="23031-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="23031-128">`as` kalıp</span><span class="sxs-lookup"><span data-stu-id="23031-128">`as` pattern</span></span>|<span data-ttu-id="23031-129">*tanımlayıcı* olarak *model*</span><span class="sxs-lookup"><span data-stu-id="23031-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="23031-130">VEYA desenli</span><span class="sxs-lookup"><span data-stu-id="23031-130">OR pattern</span></span>|<span data-ttu-id="23031-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="23031-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="23031-132">VE model</span><span class="sxs-lookup"><span data-stu-id="23031-132">AND pattern</span></span>|<span data-ttu-id="23031-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="23031-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="23031-134">Dezavantajla</span><span class="sxs-lookup"><span data-stu-id="23031-134">Cons pattern</span></span>|<span data-ttu-id="23031-135">*tanımlayıcı* :: *list-Identifier*</span><span class="sxs-lookup"><span data-stu-id="23031-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="23031-136">Liste kalıbı</span><span class="sxs-lookup"><span data-stu-id="23031-136">List pattern</span></span>|<span data-ttu-id="23031-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="23031-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="23031-138">Dizi düzeni</span><span class="sxs-lookup"><span data-stu-id="23031-138">Array pattern</span></span>|<span data-ttu-id="23031-139">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="23031-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="23031-140">Parantez içine alınmış desenler</span><span class="sxs-lookup"><span data-stu-id="23031-140">Parenthesized pattern</span></span>|<span data-ttu-id="23031-141">( *model* )</span><span class="sxs-lookup"><span data-stu-id="23031-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="23031-142">Tanımlama grubu düzeni</span><span class="sxs-lookup"><span data-stu-id="23031-142">Tuple pattern</span></span>|<span data-ttu-id="23031-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="23031-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="23031-144">Kayıt stili</span><span class="sxs-lookup"><span data-stu-id="23031-144">Record pattern</span></span>|<span data-ttu-id="23031-145">{ *Identifier1*  =  *pattern_1*; ... ; *identifier_n*  =  *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="23031-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="23031-146">Joker karakter stili</span><span class="sxs-lookup"><span data-stu-id="23031-146">Wildcard pattern</span></span>|<span data-ttu-id="23031-147">_</span><span class="sxs-lookup"><span data-stu-id="23031-147">_</span></span>|`_`|
|<span data-ttu-id="23031-148">Tür ek açıklaması ile birlikte desenler</span><span class="sxs-lookup"><span data-stu-id="23031-148">Pattern together with type annotation</span></span>|<span data-ttu-id="23031-149">*model* : *tür*</span><span class="sxs-lookup"><span data-stu-id="23031-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="23031-150">Test modelini yazın</span><span class="sxs-lookup"><span data-stu-id="23031-150">Type test pattern</span></span>|<span data-ttu-id="23031-151">:?</span><span class="sxs-lookup"><span data-stu-id="23031-151">:?</span></span> <span data-ttu-id="23031-152">*tür* [as *Identifier* ]</span><span class="sxs-lookup"><span data-stu-id="23031-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="23031-153">Null desenli</span><span class="sxs-lookup"><span data-stu-id="23031-153">Null pattern</span></span>|<span data-ttu-id="23031-154">null</span><span class="sxs-lookup"><span data-stu-id="23031-154">null</span></span>|`null`|
|<span data-ttu-id="23031-155">NameOf deseninin</span><span class="sxs-lookup"><span data-stu-id="23031-155">Nameof pattern</span></span>|<span data-ttu-id="23031-156">*ad ifade*</span><span class="sxs-lookup"><span data-stu-id="23031-156">*nameof expr*</span></span>|`nameof str`|

## <a name="constant-patterns"></a><span data-ttu-id="23031-157">Sabit desenler</span><span class="sxs-lookup"><span data-stu-id="23031-157">Constant Patterns</span></span>

<span data-ttu-id="23031-158">Sabit desenler sayısal, karakter ve dize değişmez değerleri, numaralandırma sabitleridir (numaralandırma türü adı dahil).</span><span class="sxs-lookup"><span data-stu-id="23031-158">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="23031-159">`match`Yalnızca sabit desenleri olan bir ifade, diğer dillerdeki Case ifadesiyle karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="23031-159">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="23031-160">Giriş değişmez değerle karşılaştırılır ve Değerler eşitse, model eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23031-160">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="23031-161">Sabit değerin türü, girişin türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23031-161">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="23031-162">Aşağıdaki örnek, değişmez değer desenlerinin kullanımını gösterir ve ayrıca bir değişken deseni ve ya da deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="23031-162">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="23031-163">Sabit değer deseninin başka bir örneği, numaralandırma sabitlerine dayanan bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="23031-163">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="23031-164">Sabit Listesi sabitleri kullandığınızda numaralandırma türü adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="23031-164">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="23031-165">Tanımlayıcı desenleri</span><span class="sxs-lookup"><span data-stu-id="23031-165">Identifier Patterns</span></span>

<span data-ttu-id="23031-166">Desenler, geçerli bir tanımlayıcı oluşturan karakterlerden oluşan bir dizeyse tanımlayıcı formu, düzenin nasıl eşleştirileceği belirler.</span><span class="sxs-lookup"><span data-stu-id="23031-166">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="23031-167">Tanımlayıcı tek bir karakterden uzunsa ve büyük harfli bir karakterle başlıyorsa, derleyici tanımlayıcı düzeniyle bir eşleşme yapmayı dener.</span><span class="sxs-lookup"><span data-stu-id="23031-167">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="23031-168">Bu düzenin tanımlayıcısı, değişmez değer özniteliğiyle, ayırt edici birleşim durumuyla, özel durum tanımlayıcısıyla veya etkin bir model durumuyla işaretlenmiş bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="23031-168">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="23031-169">Eşleşen bir tanımlayıcı bulunamazsa, eşleşme başarısız olur ve sonraki model kuralı, değişken deseninin girişi ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="23031-169">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="23031-170">Ayırt edici bileşim desenleri basit adlandırılmış durumlar olabilir veya bir değer ya da birden çok değer içeren bir tanımlama grubu olabilir.</span><span class="sxs-lookup"><span data-stu-id="23031-170">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="23031-171">Bir değer varsa, değer için bir tanımlayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="23031-171">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="23031-172">Bir tanımlama grubu söz konusu olduğunda, bir veya daha fazla adlandırılmış UNION alanı için, kayıt düzeninin her öğesi için tanımlayıcı veya bir alan adı olan bir tanımlayıcı içeren bir tanımlama grubu düzeni sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="23031-172">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="23031-173">Örnekler için bu bölümdeki kod örneklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="23031-173">See the code examples in this section for examples.</span></span>

<span data-ttu-id="23031-174">`option`Türü, iki durum ve içeren ayrılmış bir birleşimdir `Some` `None` .</span><span class="sxs-lookup"><span data-stu-id="23031-174">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="23031-175">Bir Case ( `Some` ) bir değere sahiptir, ancak diğeri ( `None` ) yalnızca adlandırılmış bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="23031-175">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="23031-176">Bu nedenle, `Some` servis talebiyle ilişkili değer için bir değişkene sahip olması gerekir `Some` , ancak `None` kendisi tarafından görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="23031-176">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="23031-177">Aşağıdaki kodda değişkenine, `var1` servis talebiyle eşleştirerek elde edilen değer verilir `Some` .</span><span class="sxs-lookup"><span data-stu-id="23031-177">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="23031-178">Aşağıdaki örnekte, `PersonName` ayırt edici bileşim, olası ad biçimlerini temsil eden dizelerin ve karakterlerin bir karışımını içerir.</span><span class="sxs-lookup"><span data-stu-id="23031-178">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="23031-179">Ayırt edici birleşimin durumları, ve ' dir `FirstOnly` `LastOnly` `FirstLast` .</span><span class="sxs-lookup"><span data-stu-id="23031-179">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="23031-180">Adlandırılmış alanları olan ayrılmış birleşimler için, adlandırılmış bir alanın değerini çıkarmak için eşittir işaretini (=) kullanın.</span><span class="sxs-lookup"><span data-stu-id="23031-180">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="23031-181">Örneğin, aşağıdaki gibi bir bildirime sahip ayrılmış bir birleşim düşünün.</span><span class="sxs-lookup"><span data-stu-id="23031-181">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="23031-182">Bir model eşleştirme ifadesinde adlandırılmış alanları aşağıdaki gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23031-182">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="23031-183">Adlandırılmış alanın kullanımı isteğe bağlıdır, bu nedenle önceki örnekte, her ikisi de `Circle(r)` `Circle(radius = r)` aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="23031-183">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="23031-184">Birden çok alan belirttiğinizde, noktalı virgül kullanın (;) ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="23031-184">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="23031-185">Etkin desenler, daha karmaşık özel desen eşleştirmeyi tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="23031-185">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="23031-186">Etkin desenler hakkında daha fazla bilgi için bkz. [Etkin desenler](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="23031-186">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="23031-187">Tanımlayıcının özel durum olduğu durum, özel durum işleyicileri bağlamında model eşleştirme içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-187">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="23031-188">Özel durum işlemede model eşleştirme hakkında daha fazla bilgi için bkz. [özel durumlar: `try...with` ifade](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="23031-188">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="23031-189">Değişken desenleri</span><span class="sxs-lookup"><span data-stu-id="23031-189">Variable Patterns</span></span>

<span data-ttu-id="23031-190">Değişken stili, bir değişken adıyla eşleştirildiği değeri atar ve bu daha sonra simgenin sağ tarafındaki yürütme ifadesinde kullanıma sunulmuştur `->` .</span><span class="sxs-lookup"><span data-stu-id="23031-190">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="23031-191">Bir değişken deseni her türlü girişle eşleşir, ancak değişken desenleri genellikle diğer desenlerde görünür, bu nedenle, değişkenlere ve dizilere gibi daha karmaşık yapıların bağımsız değişkenlere çıkarılması mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="23031-191">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="23031-192">Aşağıdaki örnek, bir demet deseninin içindeki değişken bir düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="23031-192">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="23031-193">as model</span><span class="sxs-lookup"><span data-stu-id="23031-193">as Pattern</span></span>

<span data-ttu-id="23031-194">`as`Bu model, kendisine eklenmiş bir yan tümcesine sahip bir modeldir `as` .</span><span class="sxs-lookup"><span data-stu-id="23031-194">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="23031-195">`as`Yan tümcesi, eşleşen değeri bir ifadenin yürütme ifadesinde kullanılabilecek bir ada bağlar `match` veya bu düzenin bir bağlamada kullanıldığı durumda `let` , ad yerel kapsama bir bağlama olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="23031-195">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="23031-196">Aşağıdaki örnek bir model kullanır `as` .</span><span class="sxs-lookup"><span data-stu-id="23031-196">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="23031-197">VEYA desenli</span><span class="sxs-lookup"><span data-stu-id="23031-197">OR Pattern</span></span>

<span data-ttu-id="23031-198">OR deseni, giriş verileri birden çok desenle eşleşiyorsa ve sonuç olarak aynı kodu yürütmek istiyorsanız kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-198">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="23031-199">YA da deseninin her iki tarafının türleri uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23031-199">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="23031-200">Aşağıdaki örnek, veya modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23031-200">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="23031-201">VE model</span><span class="sxs-lookup"><span data-stu-id="23031-201">AND Pattern</span></span>

<span data-ttu-id="23031-202">VE deseni, girişin iki desenle eşleşmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="23031-202">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="23031-203">VE deseninin her iki tarafının türleri uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23031-203">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="23031-204">Aşağıdaki örnek, `detectZeroTuple` Bu konunun ilerleyen kısımlarında yer aldığı, ancak her ikisi de ve `var1` `var2` düzeni kullanılarak değer olarak elde edilen demet düzeni bölümünde gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="23031-204">The following example is like `detectZeroTuple` shown in the Tuple Pattern section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="23031-205">Dezavantajla</span><span class="sxs-lookup"><span data-stu-id="23031-205">Cons Pattern</span></span>

<span data-ttu-id="23031-206">Cons stili, bir listeyi ilk öğe, *baş* ve geri kalan öğeleri içeren bir liste, *tail* ve bir liste için bir liste oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-206">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="23031-207">Liste kalıbı</span><span class="sxs-lookup"><span data-stu-id="23031-207">List Pattern</span></span>

<span data-ttu-id="23031-208">Liste deseninin, listelerin bir dizi öğe halinde çıkarılması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="23031-208">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="23031-209">Liste deseninin kendisi yalnızca belirli sayıdaki öğelerin listeleriyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23031-209">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="23031-210">Dizi düzeni</span><span class="sxs-lookup"><span data-stu-id="23031-210">Array Pattern</span></span>

<span data-ttu-id="23031-211">Dizi düzeni liste düzenine benzer ve belirli uzunluktaki dizileri ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="23031-211">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="23031-212">Parantez içine alınmış desenler</span><span class="sxs-lookup"><span data-stu-id="23031-212">Parenthesized Pattern</span></span>

<span data-ttu-id="23031-213">Parantezler, istenen ilişkilendirilebilirliği elde etmek için desenlerin etrafında gruplandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="23031-213">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="23031-214">Aşağıdaki örnekte, parantez ve bir dezavantajla arasındaki ilişkilendirilebilirlik denetlemek için parantezler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-214">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="23031-215">Tanımlama grubu düzeni</span><span class="sxs-lookup"><span data-stu-id="23031-215">Tuple Pattern</span></span>

<span data-ttu-id="23031-216">Tanımlama grubu düzeni, kayıt düzeni formundaki giriş ile eşleşir ve kayıt düzeninin her bir konum için model eşleme değişkenlerini kullanarak kendi bileşen öğelerine parçalanmak üzere etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="23031-216">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="23031-217">Aşağıdaki örnek demet desenini gösterir ve aynı zamanda değişmez desenleri, değişken desenleri ve joker karakter desenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23031-217">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="23031-218">Kayıt stili</span><span class="sxs-lookup"><span data-stu-id="23031-218">Record Pattern</span></span>

<span data-ttu-id="23031-219">Kayıt stili, alanların değerlerini ayıklamak için kayıt oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-219">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="23031-220">Düzenin kaydın tüm alanlarına başvurması gerekmez; Atlanan tüm alanlar yalnızca eşleştirmeye katılmaz ve ayıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="23031-220">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="23031-221">Joker karakter stili</span><span class="sxs-lookup"><span data-stu-id="23031-221">Wildcard Pattern</span></span>

<span data-ttu-id="23031-222">Joker karakter stili, alt çizgi ( `_` ) karakteriyle temsil edilir ve tıpkı değişken düzeniyle benzer şekilde, girişin bir değişkene atanması yerine atılmasının dışında herhangi bir girişle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23031-222">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="23031-223">Joker karakter deseni genellikle diğer desenlerin içinde, simgenin sağındaki ifadede gerekli olmayan değerler için yer tutucu olarak kullanılır `->` .</span><span class="sxs-lookup"><span data-stu-id="23031-223">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="23031-224">Joker karakter deseni, eşleşmeyen herhangi bir girişi eşleştirmek için bir desen listesinin sonunda da sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-224">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="23031-225">Bu konudaki çok sayıda kod örneğinde joker karakter deseninin gösterildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="23031-225">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="23031-226">Bir örnek için yukarıdaki koda bakın.</span><span class="sxs-lookup"><span data-stu-id="23031-226">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="23031-227">Tür ek açıklamalarına sahip desenler</span><span class="sxs-lookup"><span data-stu-id="23031-227">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="23031-228">Desenlerin tür ek açıklamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="23031-228">Patterns can have type annotations.</span></span> <span data-ttu-id="23031-229">Bunlar diğer tür ek açıklamaları ve diğer tür ek açıklamaları gibi kılavuz çıkarımı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="23031-229">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="23031-230">Desenlerdeki tür ek açıklamaları etrafında parantezler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="23031-230">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="23031-231">Aşağıdaki kod, tür ek açıklamasına sahip bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="23031-231">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="23031-232">Test modelini yazın</span><span class="sxs-lookup"><span data-stu-id="23031-232">Type Test Pattern</span></span>

<span data-ttu-id="23031-233">Tür Test deseninin girişi bir türle eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-233">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="23031-234">Giriş türü, düzende belirtilen tür ile bir eşleşmedir (veya türetilmiş bir tür), eşleşme başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="23031-234">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="23031-235">Aşağıdaki örnek, tür testi modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23031-235">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

<span data-ttu-id="23031-236">Yalnızca bir tanımlayıcının belirli bir türetilmiş türde olup olmadığını denetyorsanız, `as identifier` Aşağıdaki örnekte gösterildiği gibi, düzenin bir bölümüne ihtiyacınız yoktur:</span><span class="sxs-lookup"><span data-stu-id="23031-236">If you're only checking if an identifier is of a particular derived type, you don't need the `as identifier` part of the pattern, as shown in the following example:</span></span>

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

## <a name="null-pattern"></a><span data-ttu-id="23031-237">Null desenli</span><span class="sxs-lookup"><span data-stu-id="23031-237">Null Pattern</span></span>

<span data-ttu-id="23031-238">Null değer, null değere izin veren türlerle çalışırken görünebilen null değeriyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23031-238">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="23031-239">.NET Framework kodla birlikte çalışırken genellikle null desenler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23031-239">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="23031-240">Örneğin, bir .NET API 'nin dönüş değeri bir ifadenin girdisi olabilir `match` .</span><span class="sxs-lookup"><span data-stu-id="23031-240">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="23031-241">Program akışını, dönüş değerinin null ve ayrıca döndürülen değerin diğer özelliklerine göre kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23031-241">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="23031-242">Null değerlerin programınızın geri kalanına yayılmasını engellemek için null kalıbı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23031-242">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="23031-243">Aşağıdaki örnek, null ve değişken düzenlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23031-243">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="nameof-pattern"></a><span data-ttu-id="23031-244">NameOf deseninin</span><span class="sxs-lookup"><span data-stu-id="23031-244">Nameof pattern</span></span>

<span data-ttu-id="23031-245">`nameof`Değeri, anahtar sözcüğünü izleyen ifadeye eşitse, bir dizeyle eşleşir `nameof` .</span><span class="sxs-lookup"><span data-stu-id="23031-245">The `nameof` pattern matches against a string when its value is equal to the expression that follows the `nameof` keyword.</span></span> <span data-ttu-id="23031-246">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="23031-246">for example:</span></span>

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```

<span data-ttu-id="23031-247">[`nameof`](nameof.md)Ad alma hakkında bilgi için bkz. işleci.</span><span class="sxs-lookup"><span data-stu-id="23031-247">See the [`nameof`](nameof.md) operator for information on what you can take a name of.</span></span>

## <a name="see-also"></a><span data-ttu-id="23031-248">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23031-248">See also</span></span>

- [<span data-ttu-id="23031-249">Eşleşme İfadeleri</span><span class="sxs-lookup"><span data-stu-id="23031-249">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="23031-250">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="23031-250">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="23031-251">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="23031-251">F# Language Reference</span></span>](index.md)
