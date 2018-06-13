---
title: Desen Eşleştirme (F#)
description: "Desenleri F #'de mantıksal yapıları verilerle karşılaştırmak, veri bağlı parçalarına ya da verilerden bilgi ayıklamak için nasıl kullanılacağını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 64f5b2534190552db71a67b30ece41bafed3d16e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566200"
---
# <a name="pattern-matching"></a><span data-ttu-id="aafac-103">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="aafac-103">Pattern Matching</span></span>

<span data-ttu-id="aafac-104">Desenleri giriş verileri dönüştürme kurallarını alır.</span><span class="sxs-lookup"><span data-stu-id="aafac-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="aafac-105">F # dili bunlar bir mantıksal yapısını veya yapıları ile karşılaştırmak, veri bağlı parçalarına ya da verileri çeşitli yollarla bilgi ayıklamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>


## <a name="remarks"></a><span data-ttu-id="aafac-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aafac-106">Remarks</span></span>
<span data-ttu-id="aafac-107">Desenler kullanılan birçok dil yapıları gibi `match` ifade.</span><span class="sxs-lookup"><span data-stu-id="aafac-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="aafac-108">İşlevlerde bağımsız değişkenleri işlerken kullanıldıkları `let` lambda ifadeleri, bağlamaları ve ilişkili özel durum işleyiciler `try...with` ifade.</span><span class="sxs-lookup"><span data-stu-id="aafac-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="aafac-109">Daha fazla bilgi için bkz: [eşleşme ifadeleri](match-expressions.md), [let bağlamaları](functions/let-bindings.md), [Lambda ifadeleri: `fun` anahtar sözcüğü](functions/lambda-expressions-the-fun-keyword.md), ve [özel durumlar: `try...with` İfade](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="aafac-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="aafac-110">Örneğin, `match` ifadesi *düzeni* kanal simgenin aşağıda olduğu.</span><span class="sxs-lookup"><span data-stu-id="aafac-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="aafac-111">Her desen girdi şekilde dönüştürme için bir kural olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="aafac-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="aafac-112">İçinde `match` ifadesi, her düzeni incelenir sırayla giriş verilerini deseni ile uyumlu olup olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="aafac-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="aafac-113">Bir eşleşme bulunamazsa, sonuç ifadesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="aafac-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="aafac-114">Bir eşleşme bulunmazsa, sonraki düzeni kural test edilir.</span><span class="sxs-lookup"><span data-stu-id="aafac-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="aafac-115">İsteğe bağlı olduğunda *koşulu* bölümü içinde açıklanan [eşleşme ifadeleri](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="aafac-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="aafac-116">Desteklenen desenleri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aafac-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="aafac-117">Çalışma zamanında giriş her tabloda listelenen sırayla aşağıdaki desenleri karşı test ve kodunuzda ve soldan sağa desenler için her satırda göründükleri gibi desenleri uygulanan yinelemeli olarak ilk son arasındadır.</span><span class="sxs-lookup"><span data-stu-id="aafac-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="aafac-118">Ad</span><span class="sxs-lookup"><span data-stu-id="aafac-118">Name</span></span>|<span data-ttu-id="aafac-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aafac-119">Description</span></span>|<span data-ttu-id="aafac-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="aafac-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="aafac-121">Sabit düzeni</span><span class="sxs-lookup"><span data-stu-id="aafac-121">Constant pattern</span></span>|<span data-ttu-id="aafac-122">Tüm sayısal, karakter veya dize sabit değeri, bir numaralandırma sabiti veya tanımlı bir değişmez değer tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="aafac-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="aafac-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="aafac-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="aafac-124">Tanımlayıcı deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-124">Identifier pattern</span></span>|<span data-ttu-id="aafac-125">Servis talebi değerini ayrılmış UNION, bir özel durum etiketi veya bir etkin desen örneği</span><span class="sxs-lookup"><span data-stu-id="aafac-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="aafac-126">Değişken deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-126">Variable pattern</span></span>|<span data-ttu-id="aafac-127">*Tanımlayıcı*</span><span class="sxs-lookup"><span data-stu-id="aafac-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="aafac-128">`as` düzeni</span><span class="sxs-lookup"><span data-stu-id="aafac-128">`as` pattern</span></span>|<span data-ttu-id="aafac-129">*Desen* olarak *tanımlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="aafac-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="aafac-130">VEYA deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-130">OR pattern</span></span>|<span data-ttu-id="aafac-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="aafac-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="aafac-132">VE düzeni</span><span class="sxs-lookup"><span data-stu-id="aafac-132">AND pattern</span></span>|<span data-ttu-id="aafac-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="aafac-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="aafac-134">Cons deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-134">Cons pattern</span></span>|<span data-ttu-id="aafac-135">*tanımlayıcı* :: *liste tanımlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="aafac-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="aafac-136">Liste deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-136">List pattern</span></span>|<span data-ttu-id="aafac-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="aafac-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="aafac-138">Dizi deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-138">Array pattern</span></span>|<span data-ttu-id="aafac-139">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="aafac-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="aafac-140">Parantez içine alınmış desen</span><span class="sxs-lookup"><span data-stu-id="aafac-140">Parenthesized pattern</span></span>|<span data-ttu-id="aafac-141">( *düzeni* )</span><span class="sxs-lookup"><span data-stu-id="aafac-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="aafac-142">Demet deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-142">Tuple pattern</span></span>|<span data-ttu-id="aafac-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="aafac-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="aafac-144">Kayıt deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-144">Record pattern</span></span>|<span data-ttu-id="aafac-145">{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="aafac-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="aafac-146">Joker karakter deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-146">Wildcard pattern</span></span>|<span data-ttu-id="aafac-147">_</span><span class="sxs-lookup"><span data-stu-id="aafac-147">_</span></span>|`_`|
|<span data-ttu-id="aafac-148">Türü ek açıklama birlikte düzeni</span><span class="sxs-lookup"><span data-stu-id="aafac-148">Pattern together with type annotation</span></span>|<span data-ttu-id="aafac-149">*Desen* : *türü*</span><span class="sxs-lookup"><span data-stu-id="aafac-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="aafac-150">Tür test deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-150">Type test pattern</span></span>|<span data-ttu-id="aafac-151">:?</span><span class="sxs-lookup"><span data-stu-id="aafac-151">:?</span></span> <span data-ttu-id="aafac-152">*tür* [olarak *tanımlayıcısı* ]</span><span class="sxs-lookup"><span data-stu-id="aafac-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="aafac-153">Null deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-153">Null pattern</span></span>|<span data-ttu-id="aafac-154">null</span><span class="sxs-lookup"><span data-stu-id="aafac-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="aafac-155">Sabit desenleri</span><span class="sxs-lookup"><span data-stu-id="aafac-155">Constant Patterns</span></span>
<span data-ttu-id="aafac-156">Sabit desenleri sayısal karakter ve dize değişmez değerleri, numaralandırma Sabitleri (ile numaralandırma türü adı dahil) alır.</span><span class="sxs-lookup"><span data-stu-id="aafac-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="aafac-157">A `match` yalnızca sabit deseni yok ifadesi, başka dillerde case deyimi için karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="aafac-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="aafac-158">Giriş değişmez değerle karşılaştırılır ve değerleri aynıysa eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="aafac-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="aafac-159">Sabit değer türü giriş türü ile uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aafac-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="aafac-160">Aşağıdaki örnek değişmez değer desenleri kullanımını gösterir ve ayrıca bir değişken deseni ve OR deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="aafac-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="aafac-161">Değişmez değer deseni başka bir örneği üzerinde numaralandırması sabitleri dayalı bir desen bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aafac-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="aafac-162">Numaralandırma sabitleri kullandığınızda numaralandırma türü adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aafac-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="aafac-163">Tanımlayıcı desenleri</span><span class="sxs-lookup"><span data-stu-id="aafac-163">Identifier Patterns</span></span>
<span data-ttu-id="aafac-164">Desen geçerli bir tanımlayıcı forms bir karakter dizesi, formun tanımlayıcı deseni nasıl eşleştirildiği belirler.</span><span class="sxs-lookup"><span data-stu-id="aafac-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="aafac-165">Tanımlayıcı tek bir karakterden uzun ve bir büyük harf karakter ile başlar, derleyici tanımlayıcı deseni bir eşleştirme yapmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="aafac-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="aafac-166">Bu desen tanımlayıcısı değişmez değer özniteliği, ayrılmış bir bileşim durumu, bir özel durum tanımlayıcı veya etkin desen servis talebi ile işaretli bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="aafac-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="aafac-167">Eşleşen hiçbir tanımlayıcı bulunursa, eşleşmesi başarısız ve sonraki düzeni kural değişken deseni girdisi karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="aafac-168">Ayrılmış birleşim desenleri durumlarda adlı basit olabilir veya bir değer veya birden çok değer içeren bir tanımlama grubu sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aafac-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="aafac-169">Bir değer ise, değer için bir tanımlayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aafac-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="aafac-170">Bir tanımlama grubu söz konusu olduğunda kayıt her öğe için bir tanımlayıcı veya bir tanımlayıcı ile bir alan adı için bir tanımlama grubu desenle sağlamanız gerekir veya daha fazla birleşim alanları adlı.</span><span class="sxs-lookup"><span data-stu-id="aafac-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="aafac-171">Örnekler için bu bölümdeki kod örnekleri bakın.</span><span class="sxs-lookup"><span data-stu-id="aafac-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="aafac-172">`option` Türüdür iki durumda sahip ayrılmış bir birleşim `Some` ve `None`.</span><span class="sxs-lookup"><span data-stu-id="aafac-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="aafac-173">Bir örnek (`Some`) bir değer, ancak diğer sahiptir (`None`) yalnızca bir adlandırılmış bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="aafac-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="aafac-174">Bu nedenle, `Some` ile ilişkili değer için bir değişken olmalıdır `Some` durumda, ancak `None` tek başına görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="aafac-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="aafac-175">Aşağıdaki kodda, değişkeni `var1` eşleştirerek elde değeri verildiğinde `Some` durumda.</span><span class="sxs-lookup"><span data-stu-id="aafac-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="aafac-176">Aşağıdaki örnekte, `PersonName` ayrılmış birleşim dizelerini ve olası form adlarının temsil karakterleri karışımını içerir.</span><span class="sxs-lookup"><span data-stu-id="aafac-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="aafac-177">Ayrılmış birleşim örnekleri `FirstOnly`, `LastOnly`, ve `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="aafac-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="aafac-178">Alanları adlı ayrılmış birleşimler için adlandırılmış bir alanın değerini ayıklamak için eşittir işareti (=) kullanın.</span><span class="sxs-lookup"><span data-stu-id="aafac-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="aafac-179">Örneğin, bir bildirimi aşağıdaki gibi ayrılmış bir birleşim göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="aafac-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="aafac-180">Desen eşleştirme ifadesi adlandırılmış alanları gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aafac-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="aafac-181">Adlandırılmış alan kullanımı isteğe bağlıdır, bu nedenle önceki örnekte, her ikisi de `Circle(r)` ve `Circle(radius = r)` aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="aafac-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="aafac-182">Birden çok alan belirttiğinizde, noktalı virgül (;) kullanın ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="aafac-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="aafac-183">Etkin desenler daha karmaşık özel desen eşleştirme tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aafac-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="aafac-184">Etkin desenler hakkında daha fazla bilgi için bkz: [Etkin desenler](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="aafac-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="aafac-185">Tanımlayıcı bir özel durum olması durumunda, özel durum işleyicileri bağlamında eşleşen kalıbı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="aafac-186">Desen eşleştirme, özel durum işleme hakkında daha fazla bilgi için bkz: [özel durumlar: `try...with` ifade](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="aafac-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>


## <a name="variable-patterns"></a><span data-ttu-id="aafac-187">Değişken desenleri</span><span class="sxs-lookup"><span data-stu-id="aafac-187">Variable Patterns</span></span>
<span data-ttu-id="aafac-188">Değişken deseni sağındaki yürütme ifade için kullanılabilir bir değişken adı için eşleşen değeri atar `->` simgesi.</span><span class="sxs-lookup"><span data-stu-id="aafac-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="aafac-189">Herhangi bir giriş tek başına bir değişken desenle eşleşen ancak değişken desenleri genellikle bu nedenle tanımlama grupları ve değişkenlere ayrılmış dizi gibi daha karmaşık yapıları etkinleştirme diğer desenleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aafac-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="aafac-190">Aşağıdaki örnek, bir değişken deseni demet deseni içinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="aafac-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="aafac-191">as deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-191">as Pattern</span></span>
<span data-ttu-id="aafac-192">`as` Düzeni olan bir desen olan bir `as` eklenmiş yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="aafac-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="aafac-193">`as` Yan tümcesi yürütme ifadesinde kullanılabilir bir adla eşleşen değeri bağlar bir `match` ifadesi veya burada bu deseni kullanılıyor durumda bir `let` bağlama, ad yerel kapsam için bir bağlama olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="aafac-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="aafac-194">Aşağıdaki örnek kullanan bir `as` düzeni.</span><span class="sxs-lookup"><span data-stu-id="aafac-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="aafac-195">VEYA deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-195">OR Pattern</span></span>
<span data-ttu-id="aafac-196">OR deseni giriş verileri birden çok desenleri eşleşebilir ve sonuç olarak aynı kod yürütmek istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="aafac-197">OR deseni her iki tarafının türleri uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aafac-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="aafac-198">Aşağıdaki örnek, OR deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="aafac-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="aafac-199">VE düzeni</span><span class="sxs-lookup"><span data-stu-id="aafac-199">AND Pattern</span></span>
<span data-ttu-id="aafac-200">AND deseni giriş iki desen eşleşmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="aafac-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="aafac-201">Her iki tarafında ve desen türleri uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aafac-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="aafac-202">Aşağıdaki örnek benzer `detectZeroTuple` gösterilen [demet deseni](https://msdn.microsoft.com/library/#tuple) bölümünde daha sonra bu konuda, ancak burada hem `var1` ve `var2` değerler ve desen kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="aafac-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="aafac-203">Cons deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-203">Cons Pattern</span></span>
<span data-ttu-id="aafac-204">Cons deseni listesini ilk öğesine parçalayın kullanılacak *head*ve kalan öğeleri içeren bir liste *tail*.</span><span class="sxs-lookup"><span data-stu-id="aafac-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="aafac-205">Liste deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-205">List Pattern</span></span>
<span data-ttu-id="aafac-206">Liste deseni öğelerinin bir sayıya ayrılmış listelerin sağlar.</span><span class="sxs-lookup"><span data-stu-id="aafac-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="aafac-207">Liste deseni yalnızca belirli sayıda öğe listelerini eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aafac-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="aafac-208">Dizi deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-208">Array Pattern</span></span>
<span data-ttu-id="aafac-209">Dizi deseni liste deseni benzer ve belirli bir uzunlukta diziler parçalayın için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="aafac-210">Parantez içine alınmış desen</span><span class="sxs-lookup"><span data-stu-id="aafac-210">Parenthesized Pattern</span></span>
<span data-ttu-id="aafac-211">Parantez istenen birleşim elde etmek için desenleri gruplandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="aafac-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="aafac-212">Aşağıdaki örnekte, parantez birleşim ve düzeni ve dezavantajlarını düzeni arasında denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="aafac-213">Demet deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-213">Tuple Pattern</span></span>
<span data-ttu-id="aafac-214">Demet deseni tanımlama grubu formundaki girişi ile eşleşen ve bağlı elemanlara değişkenleri tanımlama grubundaki her konum için eşleşen kalıbı kullanarak ayrılmış tanımlama grubu sağlar.</span><span class="sxs-lookup"><span data-stu-id="aafac-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="aafac-215">Aşağıdaki örnek demet deseni gösterir ve ayrıca değişmez değer desenleri, değişken desenleri ve joker karakter deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="aafac-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="aafac-216">Kayıt deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-216">Record Pattern</span></span>
<span data-ttu-id="aafac-217">Kayıt deseni alanların değerlerini ayıklamak için kayıtları parçalayın için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="aafac-218">Desen kaydının tüm alanlar başvurusu gerekmez; Atlanan tüm alanlar yalnızca eşleşen içinde yer almayan ve değil ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="aafac-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="aafac-219">Joker karakter deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-219">Wildcard Pattern</span></span>
<span data-ttu-id="aafac-220">Joker karakter deseni çizgiyle gösterilir (`_`) karakter ve eşleştiğini değişken deseni gibi herhangi bir giriş giriş yerine bir değişkenine atanan atılır dışında.</span><span class="sxs-lookup"><span data-stu-id="aafac-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="aafac-221">Joker karakter deseni genellikle diğer desenleri içinde yer tutucu olarak sağındaki ifadesinde gerekli olmayan değerleri için kullanılan `->` simgesi.</span><span class="sxs-lookup"><span data-stu-id="aafac-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="aafac-222">Joker karakter deseni eşleşmeyen herhangi bir giriş eşleşecek şekilde desenlerinin bir listesi sonunda Ayrıca sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="aafac-223">Joker karakter deseni birçok kod örnekleri bu konuda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aafac-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="aafac-224">Önceki kod bir örnek için bkz.</span><span class="sxs-lookup"><span data-stu-id="aafac-224">See the preceding code for one example.</span></span>


## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="aafac-225">Tür ek açıklamaları sahip desenleri</span><span class="sxs-lookup"><span data-stu-id="aafac-225">Patterns That Have Type Annotations</span></span>
<span data-ttu-id="aafac-226">Desenler tür ek açıklamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="aafac-226">Patterns can have type annotations.</span></span> <span data-ttu-id="aafac-227">Bu diğer tür ek açıklamaları gibi davranır ve diğer tür ek açıklamaları gibi çıkarım Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="aafac-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="aafac-228">Parantez desenleri türü ek açıklamalar geçici gereklidir.</span><span class="sxs-lookup"><span data-stu-id="aafac-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="aafac-229">Aşağıdaki kod türü ek açıklama olan bir desen gösterir.</span><span class="sxs-lookup"><span data-stu-id="aafac-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="aafac-230">Tür Test deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-230">Type Test Pattern</span></span>
<span data-ttu-id="aafac-231">Tür test deseni giriş türü karşı eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="aafac-232">Giriş türü için bir eşleşme (veya türetilmiş bir tür) ise deseni, eşleşme belirtilen tür başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="aafac-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="aafac-233">Aşağıdaki örnek, tür test deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="aafac-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="aafac-234">Null deseni</span><span class="sxs-lookup"><span data-stu-id="aafac-234">Null Pattern</span></span>
<span data-ttu-id="aafac-235">Null deseni bir null değere izin türleri ile çalışırken, görünen null değerle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="aafac-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="aafac-236">Null desenleri, .NET Framework kod ile birlikte çalışırken sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aafac-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="aafac-237">Örneğin, bir .NET API dönüş değeri girdisi olabilir bir `match` ifade.</span><span class="sxs-lookup"><span data-stu-id="aafac-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="aafac-238">Program akışı dönüş değeri null olup olmadığını ve aynı zamanda döndürülen değerin diğer özelliklere göre kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aafac-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="aafac-239">Null deseni null değerler programınızı geri kalanı için yayılmasını önlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aafac-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="aafac-240">Aşağıdaki örnek, null deseni ve değişken deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="aafac-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="aafac-241">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aafac-241">See Also</span></span>
[<span data-ttu-id="aafac-242">Eşleşme İfadeleri</span><span class="sxs-lookup"><span data-stu-id="aafac-242">Match Expressions</span></span>](match-expressions.md)

[<span data-ttu-id="aafac-243">Etkin Desenler</span><span class="sxs-lookup"><span data-stu-id="aafac-243">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="aafac-244">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="aafac-244">F# Language Reference</span></span>](index.md)
