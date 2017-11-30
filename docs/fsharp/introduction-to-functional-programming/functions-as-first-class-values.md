---
title: "İlk Sınıf Değerleri Olarak İşlevler (F#)"
description: "F # programlama dili birinci sınıf durumuna işlevleri nasıl yükseltilir öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="9aa0b-104">İlk Sınıf Değerleri Olarak İşlevler</span><span class="sxs-lookup"><span data-stu-id="9aa0b-104">Functions as First-Class Values</span></span>

<span data-ttu-id="9aa0b-105">Bir tanımlama işlevsel programlama dilleri, birinci sınıf durumuna işlevlerin özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-105">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="9aa0b-106">Bir işlev ne olursa olsun, diğer yerleşik türleri değerlerle yapın ve karşılaştırılabilir çaba işlevle yapabilmek yapmak olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-106">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="9aa0b-107">İlk sınıf durumu tipik önlemleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="9aa0b-107">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="9aa0b-108">İşlev tanımlayıcıları için bağlayabilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="9aa0b-108">Can you bind functions to identifiers?</span></span> <span data-ttu-id="9aa0b-109">Diğer bir deyişle, bunları adları verebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="9aa0b-109">That is, can you give them names?</span></span>

- <span data-ttu-id="9aa0b-110">Bir liste gibi veri yapılarını işlevlerde depolayabilir miyim?</span><span class="sxs-lookup"><span data-stu-id="9aa0b-110">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="9aa0b-111">Bir işlev çağrısı bir bağımsız değişken olarak bir işlev geçirebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="9aa0b-111">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="9aa0b-112">Bir işlev çağrısında bir işlev dönebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="9aa0b-112">Can you return a function from a function call?</span></span>

<span data-ttu-id="9aa0b-113">Son iki önlem ne olarak da bilinir tanımlar *daha yüksek sıralı işlemleri* veya *daha yüksek sıralı işlevler*.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-113">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="9aa0b-114">Daha yüksek sıralı işlevler işlevleri bağımsız değişkenler olarak kabul edin ve işlevleri işlev çağrılarını değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-114">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="9aa0b-115">Bu işlemler programlamanınnın işlevler ve işlevlerin oluşturulması eşleme olarak işlevsel programlama desteği.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-115">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="9aa0b-116">Değer bir ad verin</span><span class="sxs-lookup"><span data-stu-id="9aa0b-116">Give the Value a Name</span></span>

<span data-ttu-id="9aa0b-117">Bir işlev birinci sınıf bir değerse yalnızca tamsayı, dizeler ve diğer yerleşik türleri adlandırabilirsiniz, ad mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-117">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="9aa0b-118">Bu tanımlayıcı bir değere bağlama olarak işlevsel programlama belgeleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-118">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="9aa0b-119">F # kullanan [ `let` bağlamaları](../language-reference/functions/let-bindings.md) adlarını değerlere bağlamak için: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-119">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="9aa0b-120">Aşağıdaki kod iki örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-120">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="9aa0b-121">Bir işlev gibi kolayca adı verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-121">You can name a function just as easily.</span></span> <span data-ttu-id="9aa0b-122">Aşağıdaki örnek adlı bir işlev tanımlar `squareIt` tanımlayıcısı bağlayarak `squareIt` için [lambda ifadesi](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-122">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="9aa0b-123">İşlev `squareIt` parametresinin, `n`, ve o parametrenin karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-123">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="9aa0b-124">F # aşağıdakileri sağlar daha az yazarak ile aynı sonucu elde etmek için daha az sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-124">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="9aa0b-125">İlk stili, çoğunlukla izleyin örnekleri kullanmak `let <function-name> = <lambda-expression>`işlevlerin ve bildirimi diğer türlerin değerleri arasındaki benzerlikler vurgulamak için.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-125">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="9aa0b-126">Ancak, tüm adlandırılmış işlevler kısa sözdizimi ile yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-126">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="9aa0b-127">Bazı örnekler, her iki yolla da yazılır.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-127">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="9aa0b-128">Bir veri yapısında değerini depolama</span><span class="sxs-lookup"><span data-stu-id="9aa0b-128">Store the Value in a Data Structure</span></span>

<span data-ttu-id="9aa0b-129">İlk sınıf değeri veri yapısı içinde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-129">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="9aa0b-130">Aşağıdaki kod, listeler ve diziler değerlerini depolamak örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-130">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="9aa0b-131">Bir tanımlama grubu içinde depolanan bir işlev adı bir işleve aslında değerlendirildiğini doğrulamak için aşağıdaki örnekte kullanır `fst` ve `snd` tanımlama grubundan birinci ve ikinci öğeleri ayıklamak için işleçleri `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-131">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="9aa0b-132">Tanımlama grubundaki ilk öğe `squareIt` ve ikinci öğedir `num`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-132">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="9aa0b-133">Tanımlayıcı `num` tamsayı 10 ' geçerli bir bağımsız değişken için bir önceki örnekte bağlı `squareIt` işlevi.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-133">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="9aa0b-134">İkinci ifade dizideki ikinci öğe dizideki ilk öğe uygulandığı: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-134">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="9aa0b-135">Benzer şekilde, tanımlayıcı olarak yalnızca `num` ve tamsayı 10 birbirinin yerine kullanıldığında, bu nedenle tanımlayıcısı için `squareIt` ve lambda ifadesi `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-135">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="9aa0b-136">Değer bağımsız değişken olarak geçirin</span><span class="sxs-lookup"><span data-stu-id="9aa0b-136">Pass the Value as an Argument</span></span>

<span data-ttu-id="9aa0b-137">Bir değeri bir dilde birinci sınıf durumu varsa bir işleve bağımsız değişken olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-137">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="9aa0b-138">Örneğin, tamsayıları ve dizeleri bağımsız değişken olarak geçirmek yaygındır.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-138">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="9aa0b-139">Aşağıdaki kod tamsayılar ve F # bağımsız değişken olarak geçirilen dizelere gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-139">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="9aa0b-140">İşlevler birinci sınıf durumu varsa, bunları bağımsız değişken olarak aynı şekilde geçirebilmek için olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-140">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="9aa0b-141">Bu daha yüksek sıralı işlevlerin ilk özelliği olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-141">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="9aa0b-142">Aşağıdaki örnekte, işlev `applyIt` iki parametreye sahip `op` ve `arg`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-142">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="9aa0b-143">Bir parametre için olan bir işlev gönderme `op` ve işlevi için uygun bir bağımsız değişken `arg`, işlevi uygulanıyor sonucunu döndürür `op` için `arg`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-143">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="9aa0b-144">Aşağıdaki örnekte, işlev bağımsız değişkeni ve tamsayı bağımsız değişkeni aynı şekilde adları kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-144">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="9aa0b-145">Bir işlevin başka bir işleve bağımsız değişken olarak gönderme olanağı map veya filtre işlemleri gibi işlevsel programlama dillerinde ortak soyutlamalar vurgular.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-145">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="9aa0b-146">Map işlemi, örneğin, bir listeyi gözden geçirip, her öğe için bir şeyler ve sonuçları listesinin döndürülmesi işlevler tarafından paylaşılan hesaplamaları yakalayan bir daha yüksek sıralı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-146">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="9aa0b-147">Tamsayı, listesi her bir öğesinde Artır veya her öğenin karesini veya dizelerinin listesini her bir öğesinde büyük harfe değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-147">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="9aa0b-148">Hesaplamanın hataya yatkın bölümü listesi kullanılarak bu adımları özyinelemeli işlemdir ve sonuçları döndürmek için bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-148">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="9aa0b-149">Bu bölümü eşleme işlevinde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-149">That part is captured in the mapping function.</span></span> <span data-ttu-id="9aa0b-150">Belirli bir uygulama için yazılması gereken tek şey, her liste öğesi için ayrı ayrı uygulamak istediğiniz işlevi (ekleme, karesini, durum değiştirme).</span><span class="sxs-lookup"><span data-stu-id="9aa0b-150">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="9aa0b-151">İşlev gibi eşleme işleve bağımsız değişken olarak gönderilir `squareIt` gönderilir `applyIt` önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-151">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="9aa0b-152">F # dahil olmak üzere çoğu koleksiyon türü için map yöntemlerini sağlar [listeler](../language-reference/lists.md), [diziler](../language-reference/arrays.md), ve [sıraları](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="9aa0b-152">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="9aa0b-153">Aşağıdaki örnekler listelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-153">The following examples use lists.</span></span> <span data-ttu-id="9aa0b-154">Sözdizimi `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-154">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="9aa0b-155">Daha fazla bilgi için bkz: [listeler](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="9aa0b-155">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="9aa0b-156">Bir işlev çağrısının dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9aa0b-156">Return the Value from a Function Call</span></span>

<span data-ttu-id="9aa0b-157">Bir işlev bir dilde birinci sınıf durumu varsa, yalnızca tamsayı ve dizeler gibi diğer türleri dönüş son olarak, bir işlev çağrısı değeri olarak iade etme olanağınız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-157">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="9aa0b-158">Aşağıdaki işlev çağrıları tamsayılar döner ve bunları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-158">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="9aa0b-159">Aşağıdaki işlev çağrısı bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-159">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="9aa0b-160">Satır içi tanımlanmış aşağıdaki işlev çağrısı bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-160">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="9aa0b-161">Görüntülenen değer `True`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-161">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="9aa0b-162">Bir işlev çağrısı değeri olarak bir işlev döndürme özelliği, daha yüksek sıralı işlevler ikinci özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-162">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="9aa0b-163">Aşağıdaki örnekte, `checkFor` tek bir bağımsız değişken bir işlevi olarak tanımlanan `item`ve yeni bir işlev değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-163">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="9aa0b-164">Döndürülen işlev, bağımsız değişkeni olarak bir liste alır `lst`ve arar `item` içinde `lst`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-164">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="9aa0b-165">Varsa `item` işlevi döndürür, varsa `true`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-165">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="9aa0b-166">Varsa `item` işlevi döndürür, yok `false`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-166">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="9aa0b-167">Önceki bölümde olduğu gibi aşağıdaki kod sağlanan liste işlevini kullanır [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), listeyi aramak için.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-167">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="9aa0b-168">Aşağıdaki kod `checkFor` bir bağımsız değişken, bir listesi ve 7 arar listede geçen yeni bir işlev oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-168">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="9aa0b-169">Aşağıdaki örnek işlevleri birinci sınıf durumunu F #'de, bir işlev bildirmek için kullanır `compose`, ve iki işlevi bağımsız değişkeninin birleşimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-169">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="9aa0b-170">Daha kısa bir sürüm için aşağıdaki "Curried işlevleri" bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="9aa0b-170">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="9aa0b-171">Aşağıdaki kod iki işlev bağımsız değişkenleri olarak gönderir. `compose`, her iki aynı türde tek bir bağımsız değişken almakta olan.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-171">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="9aa0b-172">Dönüş değerini iki işlev bağımsız değişkenleri oluşan bir bileşimdir yeni bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-172">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="9aa0b-173">F # iki işleç sağlar, `<<` ve `>>`, işlevleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-173">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="9aa0b-174">Örneğin, `let squareAndDouble2 = doubleIt << squareIt` eşdeğerdir `let squareAndDouble = compose doubleIt squareIt` önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-174">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="9aa0b-175">Bir işlev çağrısı değeri olarak bir işlev döndürme aşağıdaki örnekte basit bir oyun tahmin etme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-175">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="9aa0b-176">Oyun oluşturmak için arama `makeGame` değeriyle birinin tahmin etmesini istediğiniz için gönderilen `target`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-176">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="9aa0b-177">İşlev dönüş değerini `makeGame` , bir bağımsız değişken (tahmin) ve tahmin doğru olup olmadığını bildiren bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-177">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="9aa0b-178">Aşağıdaki kod çağrıları `makeGame`, değerini göndererek `7` için `target`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-178">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="9aa0b-179">Tanımlayıcı `playGame` döndürülen lambda ifadesi ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-179">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="9aa0b-180">Bu nedenle, `playGame` bağımsız değişken olarak bir değer götüren bir işlevi olduğunu `guess`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-180">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="9aa0b-181">Curried işlevleri</span><span class="sxs-lookup"><span data-stu-id="9aa0b-181">Curried Functions</span></span>

<span data-ttu-id="9aa0b-182">Birçok önceki bölümdeki örnek daha az ama öz örtük yararlanarak yazılabilir *currying* F # işlevi bildirimlerden.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-182">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="9aa0b-183">Currying her birinin tek bir parametre olan bir dizi katıştırılmış işlevlere içine birden fazla parametre olan bir işlev dönüştüren bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-183">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="9aa0b-184">F #'ta birden fazla parametre olan işlevler kendiliğinden curried haldedir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-184">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="9aa0b-185">Örneğin, `compose` aşağıdaki kısa stili üç parametre ile gösterildiği gibi önceki bölümden yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-185">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="9aa0b-186">Ancak, sonuç gösterildiği gibi bir işlevi sırayla bir parametresinin başka bir işlev döndürür bir parametre olarak döndüren bir parametrenin bir işlevi olduğunu `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-186">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="9aa0b-187">Bu işlev, çeşitli şekillerde erişebilir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-187">You can access this function in several ways.</span></span> <span data-ttu-id="9aa0b-188">Aşağıdaki örnekler her döndürür ve 18 görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-188">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="9aa0b-189">Değiştirebileceğiniz `compose4` ile `compose4curried` herhangi bir örnek.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-189">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="9aa0b-190">Önce yaptığınız gibi işlev hala çalıştığını doğrulamak için özgün test çalışmaları yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-190">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="9aa0b-191">Diziler parametrelerini kapsayan tarafından currying kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-191">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="9aa0b-192">Daha fazla bilgi için bkz: "Parametre desenleri" [parametreler ve bağımsız değişkenler](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="9aa0b-192">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="9aa0b-193">Daha kısa bir sürümünü yazmak için örtülü currying aşağıdaki örnekte kullanır `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-193">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="9aa0b-194">Nasıl ayrıntılarını `makeGame` oluşturur ve döndürür `game` işlevi bu biçimde daha az açık, ancak sonuç aynı olduğunu özgün test çalışmalarını kullanarak doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-194">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="9aa0b-195">Currying hakkında daha fazla bilgi için bkz: "Değişkenlerin kısmi uygulaması" [işlevler](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="9aa0b-195">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="9aa0b-196">Tanımlayıcı ve işlev tanımı birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-196">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="9aa0b-197">Değişken adı `num` önceki örnekler tamsayı 10 değerlendirir ve hiçbir beklenmedik biçimde olduğundan bu where `num` olan geçerli 10 de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-197">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="9aa0b-198">İşlev tanımlayıcıları ve bunların değerleri doğru aynıdır: işlevin adını kullanılabilir, herhangi bir yere bağlı lambda ifadesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-198">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="9aa0b-199">Aşağıdaki örnek tanımlayan bir `Boolean` adlı işlevi `isNegative`, işlevin adını ve işlevinin tanımı birbirinin yerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-199">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="9aa0b-200">Sonraki üç örnekler tüm döner ve görüntüler `False`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-200">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="9aa0b-201">Daha ayrıntılı bir adım öteye için değer yerine, `applyIt` için bağlı `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-201">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="9aa0b-202">İlk sınıf değerleri olarak F # işlevlerdir</span><span class="sxs-lookup"><span data-stu-id="9aa0b-202">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="9aa0b-203">Önceki bölümlerde örnekler F # işlevleri F # ilk sınıf değerleri olan ölçütlerini sağladığını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9aa0b-203">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="9aa0b-204">Bir işlev tanımı için bir tanımlayıcı bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-204">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="9aa0b-205">Veri yapısı içinde bir işlev depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-205">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="9aa0b-206">Bir işlev bağımsız değişken olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-206">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="9aa0b-207">Bir işlev çağrısı değeri olarak bir işlev geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-207">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="9aa0b-208">F # hakkında daha fazla bilgi için bkz: [F # dili başvurusu](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="9aa0b-208">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="9aa0b-209">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aa0b-209">Example</span></span>

### <a name="description"></a><span data-ttu-id="9aa0b-210">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9aa0b-210">Description</span></span>

<span data-ttu-id="9aa0b-211">Aşağıdaki kod, bu konudaki tüm örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-211">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="9aa0b-212">Kod</span><span class="sxs-lookup"><span data-stu-id="9aa0b-212">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="9aa0b-213">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9aa0b-213">See Also</span></span>

[<span data-ttu-id="9aa0b-214">Listeler</span><span class="sxs-lookup"><span data-stu-id="9aa0b-214">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="9aa0b-215">Diziler</span><span class="sxs-lookup"><span data-stu-id="9aa0b-215">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="9aa0b-216">İşlevler</span><span class="sxs-lookup"><span data-stu-id="9aa0b-216">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="9aa0b-217">`let`Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="9aa0b-217">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="9aa0b-218">Lambda ifadeleri: `fun` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="9aa0b-218">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
