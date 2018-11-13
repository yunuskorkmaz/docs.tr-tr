---
title: Desen Eşleştirme (F#)
description: Desenler F#'de mantıksal yapıları ile verileri karşılaştırmak, verileri bileşenlerine ayırmak veya verilerden bilgi ayıklamak için nasıl kullanılacağını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 5ad3d3e1a78246afdfa2948fd0fb84fa04686d30
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45991430"
---
# <a name="pattern-matching"></a><span data-ttu-id="db82c-103">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="db82c-103">Pattern Matching</span></span>

<span data-ttu-id="db82c-104">Desenler, dönüştürme giriş verileri kurallardır.</span><span class="sxs-lookup"><span data-stu-id="db82c-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="db82c-105">Bunlar, verileri mantıksal bir yapıyla veya yapılarla karşılaştırmak, verileri bileşenlerine ayırmak veya çeşitli şekillerde verilerden bilgi ayıklamak için F# dilinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="db82c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db82c-106">Remarks</span></span>

<span data-ttu-id="db82c-107">Desenler kullanılan birçok dil yapılarında gibi `match` ifade.</span><span class="sxs-lookup"><span data-stu-id="db82c-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="db82c-108">İşlevler için bağımsız değişkenler işlenirken kullanılır `let` bağlarında, lambda ifadeleri ve ilişkili özel durum işleyicileri `try...with` ifade.</span><span class="sxs-lookup"><span data-stu-id="db82c-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="db82c-109">Daha fazla bilgi için [eşleşme ifadeleri](match-expressions.md), [let bağlamaları](functions/let-bindings.md), [Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md), ve [özel durumlar: `try...with` İfade](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="db82c-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="db82c-110">Örneğin, `match` ifade *deseni* ne kanal simgesini izleyen şeydir.</span><span class="sxs-lookup"><span data-stu-id="db82c-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="db82c-111">Her desen bir şekilde girişi dönüştürme için bir kural görür.</span><span class="sxs-lookup"><span data-stu-id="db82c-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="db82c-112">İçinde `match` ifadesinde her desen incelenene sırayla giriş veri girişinin desen ile uyumlu olup olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="db82c-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="db82c-113">Bir eşleşme bulunursa sonuç ifade yürütülür.</span><span class="sxs-lookup"><span data-stu-id="db82c-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="db82c-114">Bir eşleşme bulunmazsa sonraki desen kuralı test edilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="db82c-115">İsteğe bağlı *koşul* bölümü içinde açıklanan [eşleşme ifadeleri](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="db82c-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="db82c-116">Desteklenen desenler aşağıdaki tabloda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="db82c-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="db82c-117">Çalışma zamanında giriş her biri aşağıdaki tabloda listelenen sırayla desenleri karşı test edilir ve kodunuzda ve soldan sağa doğru desenleri için her satırında göründükleri gibi desenler yinelemeli olarak uygulandığından, öncelikle son arasındadır.</span><span class="sxs-lookup"><span data-stu-id="db82c-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="db82c-118">Ad</span><span class="sxs-lookup"><span data-stu-id="db82c-118">Name</span></span>|<span data-ttu-id="db82c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db82c-119">Description</span></span>|<span data-ttu-id="db82c-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="db82c-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="db82c-121">Sabit desen</span><span class="sxs-lookup"><span data-stu-id="db82c-121">Constant pattern</span></span>|<span data-ttu-id="db82c-122">Herhangi bir sayısal, karakter veya dize sabit değeri, numaralandırma sabiti veya tanımlı bir değişmez değer tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="db82c-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="db82c-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="db82c-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="db82c-124">Tanımlayıcı desen</span><span class="sxs-lookup"><span data-stu-id="db82c-124">Identifier pattern</span></span>|<span data-ttu-id="db82c-125">Büyük/küçük harf değeri ayrılmış bir birleşim, özel durum etiketi veya etkin desen çalışması</span><span class="sxs-lookup"><span data-stu-id="db82c-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="db82c-126">Değişken deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-126">Variable pattern</span></span>|<span data-ttu-id="db82c-127">*tanımlayıcı*</span><span class="sxs-lookup"><span data-stu-id="db82c-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="db82c-128">`as` Düzeni</span><span class="sxs-lookup"><span data-stu-id="db82c-128">`as` pattern</span></span>|<span data-ttu-id="db82c-129">*Desen* olarak *tanımlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="db82c-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="db82c-130">OR deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-130">OR pattern</span></span>|<span data-ttu-id="db82c-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="db82c-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="db82c-132">VE deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-132">AND pattern</span></span>|<span data-ttu-id="db82c-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="db82c-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="db82c-134">Olumsuz desen</span><span class="sxs-lookup"><span data-stu-id="db82c-134">Cons pattern</span></span>|<span data-ttu-id="db82c-135">*tanımlayıcı* :: *liste tanımlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="db82c-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="db82c-136">Liste deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-136">List pattern</span></span>|<span data-ttu-id="db82c-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="db82c-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="db82c-138">Dizi deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-138">Array pattern</span></span>|<span data-ttu-id="db82c-139">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="db82c-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="db82c-140">Parantezlenmiş desen</span><span class="sxs-lookup"><span data-stu-id="db82c-140">Parenthesized pattern</span></span>|<span data-ttu-id="db82c-141">( *deseni* )</span><span class="sxs-lookup"><span data-stu-id="db82c-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="db82c-142">Tanımlama grubu düzeni</span><span class="sxs-lookup"><span data-stu-id="db82c-142">Tuple pattern</span></span>|<span data-ttu-id="db82c-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="db82c-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="db82c-144">Kayıt düzeni</span><span class="sxs-lookup"><span data-stu-id="db82c-144">Record pattern</span></span>|<span data-ttu-id="db82c-145">{ *ıdentifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="db82c-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="db82c-146">Joker karakter deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-146">Wildcard pattern</span></span>|<span data-ttu-id="db82c-147">_</span><span class="sxs-lookup"><span data-stu-id="db82c-147">_</span></span>|`_`|
|<span data-ttu-id="db82c-148">Tür ek açıklaması ile birlikte desenleyin</span><span class="sxs-lookup"><span data-stu-id="db82c-148">Pattern together with type annotation</span></span>|<span data-ttu-id="db82c-149">*Desen* : *türü*</span><span class="sxs-lookup"><span data-stu-id="db82c-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="db82c-150">Test desenini yazın</span><span class="sxs-lookup"><span data-stu-id="db82c-150">Type test pattern</span></span>|<span data-ttu-id="db82c-151">:?</span><span class="sxs-lookup"><span data-stu-id="db82c-151">:?</span></span> <span data-ttu-id="db82c-152">*tür* [olarak *tanımlayıcı* ]</span><span class="sxs-lookup"><span data-stu-id="db82c-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="db82c-153">Null desen</span><span class="sxs-lookup"><span data-stu-id="db82c-153">Null pattern</span></span>|<span data-ttu-id="db82c-154">null</span><span class="sxs-lookup"><span data-stu-id="db82c-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="db82c-155">Sabit desenler</span><span class="sxs-lookup"><span data-stu-id="db82c-155">Constant Patterns</span></span>

<span data-ttu-id="db82c-156">Sabit desenler sayısal, karakter ve dize değişmez değerleri, numaralandırma sabitidir (numaralandırma türü adı dahil) var.</span><span class="sxs-lookup"><span data-stu-id="db82c-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="db82c-157">A `match` yalnızca sabit desenlere sahip ifadesi, başka dillerdeki case ifadesinden karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="db82c-158">Girdi değişmez değerle karşılaştırılır ve değerleri aynıysa desen eşleşir.</span><span class="sxs-lookup"><span data-stu-id="db82c-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="db82c-159">Değişmez değerin türü giriş türü ile uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db82c-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="db82c-160">Aşağıdaki örnek, değişmez değer desenlerinin kullanımını gösterir ve ayrıca bir değişken desen ve bir veya deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="db82c-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="db82c-161">Değişmez değer deseninin başka bir örneği, numaralandırma sabitlerini temel alan bir desendir.</span><span class="sxs-lookup"><span data-stu-id="db82c-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="db82c-162">Numaralandırma sabitlerini kullandığınızda, numaralandırma türü adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="db82c-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="db82c-163">Tanımlayıcı desenler</span><span class="sxs-lookup"><span data-stu-id="db82c-163">Identifier Patterns</span></span>

<span data-ttu-id="db82c-164">Desen, geçerli bir tanımlayıcı oluşturan karakter dizesi ise tanımlayıcının biçimi desen eşleştirilmesini belirler.</span><span class="sxs-lookup"><span data-stu-id="db82c-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="db82c-165">Tanımlayıcı tek bir karakterden daha uzunsa ve büyük harfli bir karakterle başlayan, derleyici tanımlayıcı desen bir eşleştirme yapmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="db82c-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="db82c-166">Bu düzen tanımlayıcısı değişmez değer özniteliği, ayrılmış bir birleşim durumu, bir özel durum tanımlayıcısı veya etkin desen çalışması ile işaretlenmiş bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="db82c-167">Eşleşen hiçbir tanımlayıcı bulunmazsa, eşleştirme başarısız olur ve sonraki desen kuralı, değişken desen girdiyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="db82c-168">Adlandırılmış çalışmalar ayrılmış birleşim desenleri basit olabilir veya bir değer ya da birden çok değer içeren bir tanımlama grubu olabilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="db82c-169">Bir değer varsa değer için bir tanımlayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="db82c-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="db82c-170">Bir demet söz konusu olduğunda bir kayıt düzeni deseni kayıt düzeninin her öğe için bir tanımlayıcı veya bir alan adı olan bir tanımlayıcı sağlamanız gerekir veya birkaç adlandırılmış birlik alanı.</span><span class="sxs-lookup"><span data-stu-id="db82c-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="db82c-171">Kod örnekleri için bu bölümdeki örneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="db82c-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="db82c-172">`option` Türüdür iki duruma sahip ayrılmış bir birleşim `Some` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="db82c-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="db82c-173">Bir harf (`Some`) bir değer, ancak diğer sahiptir (`None`) sadece adlı bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="db82c-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="db82c-174">Bu nedenle, `Some` ilişkili değer için bir değişken olmalıdır `Some` büyük/küçük harf, ancak `None` tek başına görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="db82c-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="db82c-175">Aşağıdaki kodda, değişken `var1` için elde edilen değeri verilir `Some` çalışması.</span><span class="sxs-lookup"><span data-stu-id="db82c-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="db82c-176">Aşağıdaki örnekte, `PersonName` birleşimdir dizeleri ve olası ad formlarını temsil eden karakterler bir karışımını içerir.</span><span class="sxs-lookup"><span data-stu-id="db82c-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="db82c-177">Ayrılmış birleşimin durumları olan `FirstOnly`, `LastOnly`, ve `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="db82c-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="db82c-178">Alanları adlı ayrılmış birleşimler, eşittir işareti (=) adlı bir alanın değerini ayıklamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="db82c-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="db82c-179">Örneğin, aşağıdaki gibi bir bildirim ile ayrılmış bir birleşim göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="db82c-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="db82c-180">İfadeyle eşleşen desendeki adlandırılmış alanları aşağıdaki gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db82c-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="db82c-181">Adlandırılmış alan kullanımı isteğe bağlıdır, dolayısıyla önceki örnekte, her ikisi de `Circle(r)` ve `Circle(radius = r)` aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="db82c-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="db82c-182">Noktalı virgül (;) kullanın, birden çok alan belirtirken, ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="db82c-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="db82c-183">Etkin desenler daha karmaşık özel desen eşleştirmeleri tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="db82c-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="db82c-184">Etkin desenler hakkında daha fazla bilgi için bkz: [Etkin desenler](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="db82c-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="db82c-185">Tanımlayıcı bir özel durum olduğu durumda, özel durum işleyicilerinin bağlamında eşleşen desende kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="db82c-186">Özel Durum İşlemede desen hakkında daha fazla bilgi için bkz. [özel durumlar: `try...with` ifade](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="db82c-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="db82c-187">Değişken desenleri</span><span class="sxs-lookup"><span data-stu-id="db82c-187">Variable Patterns</span></span>

<span data-ttu-id="db82c-188">Değişken desen ardından sağındaki yürütme ifadesinde kullanılabilecek bir değişken adı, eşleştirilen değeri atar `->` simgesi.</span><span class="sxs-lookup"><span data-stu-id="db82c-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="db82c-189">Değişken desen tek başına herhangi bir girdiyle eşleşir ancak değişken desenler genellikle bu nedenle diziler ve değişkenlere ayrıştırılacak diziler gibi daha karmaşık yapıları etkinleştirme, diğer desenlerle görünür.</span><span class="sxs-lookup"><span data-stu-id="db82c-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="db82c-190">Aşağıdaki örnek, bir kayıt düzeni desen içinde değişken bir desen gösterir.</span><span class="sxs-lookup"><span data-stu-id="db82c-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="db82c-191">Deseni olarak</span><span class="sxs-lookup"><span data-stu-id="db82c-191">as Pattern</span></span>

<span data-ttu-id="db82c-192">`as` Desendir sahip bir deseni bir `as` eklenmiş yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="db82c-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="db82c-193">`as` Yan tümcesi eşleşen değeri yürütme ifadesinde kullanılabilecek bir ada bağlar bir `match` ifade veya durumda, bu düzen kullanıldığı bir `let` bağlama, ad yerel kapsama bir bağlama olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="db82c-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="db82c-194">Aşağıdaki örnekte bir `as` deseni.</span><span class="sxs-lookup"><span data-stu-id="db82c-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="db82c-195">OR deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-195">OR Pattern</span></span>

<span data-ttu-id="db82c-196">OR deseni, giriş verilerinin birden çok desen eşleştiğinde ve sonuç olarak aynı kodu yürütmek istediğiniz kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="db82c-197">VEYA deseninin her iki tarafının türleri uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db82c-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="db82c-198">Aşağıdaki örnek OR desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="db82c-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="db82c-199">VE deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-199">AND Pattern</span></span>

<span data-ttu-id="db82c-200">VE deseni girişin iki deseni eşleştirmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="db82c-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="db82c-201">VE deseninin her iki tarafının türleri uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db82c-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="db82c-202">Aşağıdaki örnek gibi `detectZeroTuple` gösterilen [kayıt düzeni deseni](https://msdn.microsoft.com/library/#tuple) bölümde daha sonra bu konuda, ancak burada her iki `var1` ve `var2` değerler ve deseni kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="db82c-203">Olumsuz desen</span><span class="sxs-lookup"><span data-stu-id="db82c-203">Cons Pattern</span></span>

<span data-ttu-id="db82c-204">Olumsuz desen, bir listeyi ilk öğeye ayırmak için kullanılan *baş*ve kalan öğeleri içeren bir liste *tail*.</span><span class="sxs-lookup"><span data-stu-id="db82c-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="db82c-205">Liste deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-205">List Pattern</span></span>

<span data-ttu-id="db82c-206">Liste deseni listelerin çeşitli öğelere ayrıştırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="db82c-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="db82c-207">Liste deseninin kendisi yalnızca belirli sayıda öğelerin listesini eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="db82c-208">Dizi deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-208">Array Pattern</span></span>

<span data-ttu-id="db82c-209">Dizi deseni liste desenine benzer ve belirli uzunlukta diziler ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="db82c-210">Parantezlenmiş desen</span><span class="sxs-lookup"><span data-stu-id="db82c-210">Parenthesized Pattern</span></span>

<span data-ttu-id="db82c-211">Parantez, istenen birleşimi elde etmek için desenler etrafında gruplandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="db82c-212">Aşağıdaki örnekte, parantezler bir AND deseni ve bir olumsuz desen arasındaki ilişkiyi denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="db82c-213">Tanımlama grubu düzeni</span><span class="sxs-lookup"><span data-stu-id="db82c-213">Tuple Pattern</span></span>

<span data-ttu-id="db82c-214">Kayıt düzeni deseni kayıt düzeni formunda bir girdiyle eşleşir ve kayıt düzenindeki her konum için değişken desen kullanarak bileşen öğelerine ayrılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="db82c-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="db82c-215">Aşağıdaki örnek, kayıt düzeni desenini gösterir ve ayrıca değişmez değer desenleri, değişken desenler ve joker karakter deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="db82c-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="db82c-216">Kayıt düzeni</span><span class="sxs-lookup"><span data-stu-id="db82c-216">Record Pattern</span></span>

<span data-ttu-id="db82c-217">Kayıt düzeni, alanların değerlerini ayıklamak üzere kayıtları ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="db82c-218">Desen, kaydın tüm alanlarını başvurmak yok; Atlanan tüm alanlar yalnızca eşleşen katılmaz ve ayıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="db82c-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="db82c-219">Joker karakter deseni</span><span class="sxs-lookup"><span data-stu-id="db82c-219">Wildcard Pattern</span></span>

<span data-ttu-id="db82c-220">Joker karakter deseni alt çizgi ile temsil edilir (`_`) karakteri ve giriş yerine bir değişkene atandığında atılır dışında tıpkı değişken desen gibi herhangi bir girişle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="db82c-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="db82c-221">Joker karakter deseni genellikle diğer desenler içinde yer tutucu olarak sağındaki ifadede gerekmeyen değerler için kullanılan `->` simgesi.</span><span class="sxs-lookup"><span data-stu-id="db82c-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="db82c-222">Joker karakter deseni, eşleşmeyen herhangi bir girişi eşleştirmek için Desen listesinin sonunda da sık sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="db82c-223">Joker karakter deseni, bu konudaki pek çok kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="db82c-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="db82c-224">Bir örnek için önceki koda bakın.</span><span class="sxs-lookup"><span data-stu-id="db82c-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="db82c-225">Tür ek açıklamaları olan desenler</span><span class="sxs-lookup"><span data-stu-id="db82c-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="db82c-226">Desenler, tür ek açıklamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="db82c-226">Patterns can have type annotations.</span></span> <span data-ttu-id="db82c-227">Bunlar diğer türden ek açıklamalar gibi davranır ve diğer türden ek açıklamalar gibi çıkarım Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="db82c-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="db82c-228">Bulunan tür ek açıklamaları etrafına parantez gereklidir.</span><span class="sxs-lookup"><span data-stu-id="db82c-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="db82c-229">Aşağıdaki kod, bir tür ek açıklamasına sahip bir deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="db82c-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="db82c-230">Test desenini yazın</span><span class="sxs-lookup"><span data-stu-id="db82c-230">Type Test Pattern</span></span>

<span data-ttu-id="db82c-231">Tür sınama deseni, girişi bir türle eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="db82c-232">Giriş türü için bir eşleşme (veya türetilmiş bir tür) ise belirtilen desen, eşleşme başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="db82c-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="db82c-233">Aşağıdaki örnek tür testi desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="db82c-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="db82c-234">Null desen</span><span class="sxs-lookup"><span data-stu-id="db82c-234">Null Pattern</span></span>

<span data-ttu-id="db82c-235">Null desen, null değere izin türleriyle çalışırken görünebilen null değer eşleşir.</span><span class="sxs-lookup"><span data-stu-id="db82c-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="db82c-236">Null desenler, .NET Framework kodu ile birlikte çalışırken sıkça kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db82c-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="db82c-237">Örneğin, bir .NET API dönüş değerini giriş olabilir bir `match` ifade.</span><span class="sxs-lookup"><span data-stu-id="db82c-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="db82c-238">Dönüş değerinin null olup olmadığını ve aynı zamanda döndürülen değerin diğer özelliklerini temel alan program akışını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db82c-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="db82c-239">Null değerler, programınızın kalanına yayılmasını önlemek için null desenini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db82c-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="db82c-240">Aşağıdaki örnek boş desen ve değişken deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="db82c-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="db82c-241">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db82c-241">See also</span></span>

- [<span data-ttu-id="db82c-242">Eşleşme İfadeleri</span><span class="sxs-lookup"><span data-stu-id="db82c-242">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="db82c-243">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="db82c-243">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="db82c-244">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="db82c-244">F# Language Reference</span></span>](index.md)
