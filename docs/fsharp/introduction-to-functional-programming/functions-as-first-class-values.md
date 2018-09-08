---
title: İlk Sınıf Değerleri Olarak İşlevler (F#)
description: 'İşlevler F # programlama dilinin birinci sınıf durumuna nasıl yükseltilir öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 45b65ab2454a592d38c80fd367e7243635614727
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195848"
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="c9ed9-103">İlk Sınıf Değerleri Olarak İşlevler</span><span class="sxs-lookup"><span data-stu-id="c9ed9-103">Functions as First-Class Values</span></span>

<span data-ttu-id="c9ed9-104">Bir tanımlama işlevsel programlama dilleri, birinci sınıf durum işlevlerin özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="c9ed9-105">Bir işlev ile ne olursa olsun, diğer yerleşik türlerin değerlerle yapın ve bunu karşılaştırılabilir düzeyde çaba yapabilmek yapmak.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="c9ed9-106">Birinci sınıf durumunu tipik ölçüler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="c9ed9-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="c9ed9-107">İşlev tanımlayıcıları için bağlayabilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="c9ed9-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="c9ed9-108">Diğer bir deyişle, bunları adlar verebilir misiniz?</span><span class="sxs-lookup"><span data-stu-id="c9ed9-108">That is, can you give them names?</span></span>

- <span data-ttu-id="c9ed9-109">Bir liste gibi veri yapıları işlevlerde depolayabilir miyim?</span><span class="sxs-lookup"><span data-stu-id="c9ed9-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="c9ed9-110">Bir işlev çağrısında bağımsız değişken olarak bir işlev geçirebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="c9ed9-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="c9ed9-111">Bir işlev çağrısında bir işlev iade edebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="c9ed9-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="c9ed9-112">Son iki ölçü olarak bilinen ne tanımlamak *daha yüksek sıralı işlemler* veya *daha yüksek sıralı işlev*.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="c9ed9-113">Daha yüksek sıralı işlev, işlev bağımsız değişkenleri olarak kabul edin ve İşlevler işlev çağrılarının değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="c9ed9-114">Bu işlemleri gibi kavramanızı işlevleri ve işlevlerin oluşturulması eşleme olarak işlevsel programlama desteği.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="c9ed9-115">Değer bir ad verin</span><span class="sxs-lookup"><span data-stu-id="c9ed9-115">Give the Value a Name</span></span>

<span data-ttu-id="c9ed9-116">Birinci sınıf bir değer bir işlev ise tam sayılar, dizeler ve diğer yerleşik türler yalnızca ad verebilirsiniz, bunu adlandırın mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="c9ed9-117">Bu tanımlayıcının bağlama için bir değer olarak fonksiyonel programlama belgeleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="c9ed9-118">F # kullandığı [ `let` bağlamaları](../language-reference/functions/let-bindings.md) değerlere adları bağlamak için: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="c9ed9-119">Aşağıdaki kod, iki örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="c9ed9-120">Bir işlev gibi kolayca yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-120">You can name a function just as easily.</span></span> <span data-ttu-id="c9ed9-121">Aşağıdaki örnek adlı bir işlev tanımlar `squareIt` tanımlayıcı bağlayarak `squareIt` için [lambda ifadesi](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="c9ed9-122">İşlev `squareIt` bir parametresi vardır `n`, ve bu parametre karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="c9ed9-123">F # aşağıdakileri sağlar daha az yazarak ile aynı sonucu elde etmek için daha kısa bir söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="c9ed9-124">İlk stili, genellikle aşağıdaki örneklerde kullanın `let <function-name> = <lambda-expression>`işlevlerin bildirimini ve diğer değer türleri bildirimi arasındaki benzerlikler vurgulamak için.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="c9ed9-125">Bununla birlikte, adlandırılan işlevlerin kısa sözdizimi ile yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="c9ed9-126">Bazı örnekler, her iki yolla da yazılır.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="c9ed9-127">Bir veri yapısı değer Store</span><span class="sxs-lookup"><span data-stu-id="c9ed9-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="c9ed9-128">Birinci sınıf bir değer veri yapısı içinde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="c9ed9-129">Aşağıdaki kod, listeler ve dizilerde değerler depolayan örnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="c9ed9-130">Bir grup içinde depolanmış bir işlev adı, bir işleve aslında değerlendirildiğini doğrulamak için aşağıdaki örnekte `fst` ve `snd` işleçleri tanımlama grubundan birinci ve ikinci öğeleri ayıklanacak `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="c9ed9-131">Dizideki ilk öğe `squareIt` ve ikinci öğe `num`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="c9ed9-132">Tanımlayıcı `num` tamsayıya 10, geçerli bir bağımsız değişken için bir önceki örnekte bağlı `squareIt` işlevi.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="c9ed9-133">İkinci ifade düzenindeki ikinci öğe dizideki ilk öğe uygular: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="c9ed9-134">Benzer şekilde, tanımlayıcı olarak yalnızca `num` ve tamsayı 10 kullanılabileceğinden, bu nedenle tanımlayıcısı için `squareIt` ve lambda ifadesi `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="c9ed9-135">Değeri bağımsız değişken olarak geçirin</span><span class="sxs-lookup"><span data-stu-id="c9ed9-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="c9ed9-136">Değer bir dilde birinci sınıf bir durum varsa, bir işleve bağımsız değişken olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="c9ed9-137">Örneğin, tamsayılar ve dizelerin bağımsız değişken olarak geçirmek için yaygındır.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="c9ed9-138">Aşağıdaki kod, tamsayı ve F # bağımsız değişken olarak geçirilen dizeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="c9ed9-139">İşlevler, birinci sınıf bir durum varsa, bunları bağımsız değişken olarak aynı şekilde geçirebilmek için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="c9ed9-140">Bu daha yüksek sıralı işlev ilk özelliği olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="c9ed9-141">Aşağıdaki örnekte, işlev `applyIt` iki parametreye sahip `op` ve `arg`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="c9ed9-142">Bir parametre için olan bir işlev gönderme `op` ve uygun bir bağımsız değişken işleve `arg`, işlevin sonucu döndürür `op` için `arg`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="c9ed9-143">Aşağıdaki örnekte, işlev bağımsız değişkeni hem tamsayı bağımsız değişkeni aynı şekilde, adları kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="c9ed9-144">Bir işlev, başka bir işleve bağımsız değişken olarak gönderme olanağı, map veya filtre işlemleri gibi işlevsel programlama dillerinde ortak soyutlama vurgular.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="c9ed9-145">Bir harita, örneğin, bir listeyi gözden geçirip, her öğe için bir şey yapın ve ardından sonuçların listesini döndürür işlevleri tarafından paylaşılan hesaplama yakalayan bir yüksek sıralı işlev işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="c9ed9-146">Tamsayı, listedeki her öğe artırmak veya her öğe kare veya dizelerinin listesini her öğe büyük harfe değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="c9ed9-147">Hesaplama hataya parçası listesi üzerinden yinelenen işlemidir ve döndürülecek sonuçları bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="c9ed9-148">Bu bölüm, eşleme işlevinde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="c9ed9-149">Belirli bir uygulama için yazmanız şey, tek tek her liste öğesine uygulamak istediğiniz işlevi (ekleyerek, karesini, değiştirme).</span><span class="sxs-lookup"><span data-stu-id="c9ed9-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="c9ed9-150">İşlevi gibi bir eşleme işlevi için bağımsız değişken olarak gönderilir `squareIt` gönderilen `applyIt` önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="c9ed9-151">F # dahil olmak üzere çoğu koleksiyon türü için eşleme yöntemlerini sağlar [listeler](../language-reference/lists.md), [diziler](../language-reference/arrays.md), ve [dizileri](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="c9ed9-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="c9ed9-152">Aşağıdaki örnekler listeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-152">The following examples use lists.</span></span> <span data-ttu-id="c9ed9-153">Söz dizimi `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="c9ed9-154">Daha fazla bilgi için [listeler](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="c9ed9-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="c9ed9-155">Bir işlev çağrısında dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="c9ed9-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="c9ed9-156">Bir işlev bir dilde birinci sınıf bir durum varsa, tamsayılar ve dizelerin gibi diğer türleri, iade yalnızca son olarak, bir işlev çağrısı, değeri olarak geri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="c9ed9-157">Aşağıdaki işlev çağrıları, tamsayı döndüren ve bunları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="c9ed9-158">Aşağıdaki işlev çağrısı, bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="c9ed9-159">Aşağıdaki işlev çağrısı, satır içi olarak bildirilen bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="c9ed9-160">Görüntülenen değer `True`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="c9ed9-161">İşlev dönüş değeri olarak bir işlev çağrısı olanağı, daha yüksek sıralı işlev ikinci özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="c9ed9-162">Aşağıdaki örnekte, `checkFor` tek bir bağımsız değişken alan bir işlev olarak tanımlanır `item`ve yeni bir işlev değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="c9ed9-163">Döndürülen işlevi, bağımsız olarak bir liste alır `lst`ve arar `item` içinde `lst`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="c9ed9-164">Varsa `item` işlevi döndürür, varsa `true`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="c9ed9-165">Varsa `item` işlevi döndürür yoksa `false`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="c9ed9-166">Önceki bölümde gösterildiği gibi aşağıdaki kod, sağlanan liste işlevini kullanır. [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), listesinde arama yapın.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-166">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="c9ed9-167">Aşağıdaki kod `checkFor` listesinde bir bağımsız değişken listesini ve 7 arar alan yeni bir işlev oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="c9ed9-168">Aşağıdaki örnekte birinci sınıf işlevler durumunu F # bir işlevi bildirmek için kullanır `compose`, iki işlev bağımsız değişkenleri bir bileşimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]

>[!NOTE]
<span data-ttu-id="c9ed9-169">Daha kısa bir sürüm için aşağıdaki "Curried İşlevler" bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="c9ed9-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="c9ed9-170">Aşağıdaki kod iki işlev için bağımsız değişken olarak gönderir. `compose`hem aynı türde tek bir bağımsız değişken almakta olan.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="c9ed9-171">İki işlev bağımsız değişkenlerinin bir birleşimi olan yeni bir işlev dönüş değeridir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]

>[!NOTE]
<span data-ttu-id="c9ed9-172">F # sağlayan iki işleç `<<` ve `>>`, İşlevler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="c9ed9-173">Örneğin, `let squareAndDouble2 = doubleIt << squareIt` eşdeğerdir `let squareAndDouble = compose doubleIt squareIt` önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="c9ed9-174">Bir işlev çağrısı değeri olarak bir işlev döndürme aşağıdaki örnek, basit bir tahmin etme oyunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="c9ed9-175">Oyun oluşturmak için arama `makeGame` değeriyle birinin tahmin etmesini istediğiniz için gönderilen `target`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="c9ed9-176">İşlev dönüş değeri `makeGame` bir bağımsız değişken (tahmin) alır ve tahmin doğru olup olmadığını bildirir, bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="c9ed9-177">Aşağıdaki kod çağrıları `makeGame`, değerini göndererek `7` için `target`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="c9ed9-178">Tanımlayıcı `playGame` döndürülen lambda ifadesi ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="c9ed9-179">Bu nedenle, `playGame` değeri bağımsız değişken olarak alan için bir işlev, `guess`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="c9ed9-180">Curried işlevleri</span><span class="sxs-lookup"><span data-stu-id="c9ed9-180">Curried Functions</span></span>

<span data-ttu-id="c9ed9-181">Önceki bölümde yer alan örnekler birçoğu daha kısaca örtük avantajlarından yararlanarak yazılabilir *currying* F # işlev bildirimleri içinde.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="c9ed9-182">Currying her biri tek bir parametreye sahip bir dizi katıştırılmış İşlevler, birden fazla parametresi olan bir işlev dönüştüren bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="c9ed9-183">F # içinde birden fazla parametreye sahip işlevler kendiliğinden curried haldedir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="c9ed9-184">Örneğin, `compose` üç parametrelerle aşağıdaki kısa stili gösterildiği gibi önceki bölümden yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="c9ed9-185">Ancak, sonuç bir gösterildiği gibi bir işlevi sırayla bir parametrenin başka bir işlev döndürür. bir parametre olarak döndüren bir parametrenin işlevidir `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="c9ed9-186">Bu işlev, çeşitli şekillerde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-186">You can access this function in several ways.</span></span> <span data-ttu-id="c9ed9-187">Her biri aşağıdaki örnekler verir ve 18 görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="c9ed9-188">Değiştirebilirsiniz `compose4` ile `compose4curried` herhangi birinde örnekler.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="c9ed9-189">Önce yaptığınız gibi işlev hala çalışır durumda olduğunu doğrulamak için özgün test çalışmalarını yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]

>[!NOTE]
<span data-ttu-id="c9ed9-190">Parametreleri de tanımlama gruplarına kapsayan tarafından currying kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="c9ed9-191">Daha fazla bilgi için bkz: "Parametre desenleri" [parametreler ve bağımsız değişkenler](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="c9ed9-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="c9ed9-192">Kullanan daha kısa bir sürümünü yazmanıza aşağıdaki örnek örtük currying `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="c9ed9-193">Nasıl ayrıntılarını `makeGame` oluşturur ve döndürür `game` işlevi bu biçimde daha az açık, ancak sonuç aynı olduğunu özgün test çalışmalarını kullanarak doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="c9ed9-194">Currying hakkında daha fazla bilgi için bkz: "Değişkenlerin kısmi uygulaması" [işlevleri](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="c9ed9-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="c9ed9-195">Tanımlayıcı ve işlev tanımı birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="c9ed9-196">Değişken adı `num` önceki örnekleri, tamsayı 10 değerlendirir ve süpriz olduğundan, nerede `num` olan geçerli 10 de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="c9ed9-197">İşlev tanımlayıcıları ve bunların değerlerini true aynıdır: bağlı lambda ifadesi işlevin adını kullanılabilir, her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="c9ed9-198">Aşağıdaki örnekte tanımlayan bir `Boolean` çağrılan işlev `isNegative`ve işlevin adını hem de işlev tanımı birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="c9ed9-199">Sonraki üç örnekler tüm geri dönün ve görüntüleme `False`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="c9ed9-200">Bir adım ileri taşımak için değeri yerine, `applyIt` için bağlı `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="c9ed9-201">İşlevler F birinci sınıf değerler\#</span><span class="sxs-lookup"><span data-stu-id="c9ed9-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="c9ed9-202">Önceki bölümlerde örneklerde, F # işlevleri ilk sınıf değerleri olarak F # olan ölçütlerini sağladığını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c9ed9-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="c9ed9-203">Tanımlayıcının bir işlev tanımı bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="c9ed9-204">Veri yapısı içinde bir işlev depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="c9ed9-205">Bir işlev bağımsız değişken olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="c9ed9-206">Bir işlev bir işlev çağrısı değeri olarak döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="c9ed9-207">F # hakkında daha fazla bilgi için bkz. [F # dili başvurusu](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="c9ed9-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="c9ed9-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9ed9-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="c9ed9-209">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9ed9-209">Description</span></span>

<span data-ttu-id="c9ed9-210">Aşağıdaki kod bu konunun tüm örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="c9ed9-211">Kod</span><span class="sxs-lookup"><span data-stu-id="c9ed9-211">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="c9ed9-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9ed9-212">See also</span></span>

- [<span data-ttu-id="c9ed9-213">Listeler</span><span class="sxs-lookup"><span data-stu-id="c9ed9-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="c9ed9-214">Demetler</span><span class="sxs-lookup"><span data-stu-id="c9ed9-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="c9ed9-215">İşlevler</span><span class="sxs-lookup"><span data-stu-id="c9ed9-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="c9ed9-216">`let` Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c9ed9-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="c9ed9-217">Lambda ifadeleri: `fun` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c9ed9-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
