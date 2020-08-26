---
title: Birinci sınıf işlevler
description: "Birinci sınıf işlevleri hakkında bilgi edinin ve bunların F # ' ta işlevsel programlama için ne kadar önemli olduğunu öğrenin."
ms.date: 10/29/2018
ms.openlocfilehash: 1dc8eae1655187282f05bf4e9501ecc8a17deba8
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810917"
---
# <a name="first-class-functions"></a><span data-ttu-id="85f54-103">Birinci sınıf işlevler</span><span class="sxs-lookup"><span data-stu-id="85f54-103">First-class functions</span></span>

<span data-ttu-id="85f54-104">İşlevsel programlama dillerinin özelliklerini tanımlama, işlevlerin birinci sınıf durumuna yükseltilmesinin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="85f54-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="85f54-105">Diğer yerleşik türlerin değerleriyle yapabileceğin bir işlev ile yapabilecekleriniz ve bunu benzer bir ölçüde çaba ile yapabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="85f54-106">Birinci sınıf durumun tipik ölçümleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="85f54-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="85f54-107">İşlevleri tanımlayıcılara bağlayabilir miyim?</span><span class="sxs-lookup"><span data-stu-id="85f54-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="85f54-108">Diğer bir deyişle, bunlara adlar verebilir misiniz?</span><span class="sxs-lookup"><span data-stu-id="85f54-108">That is, can you give them names?</span></span>

- <span data-ttu-id="85f54-109">İşlevleri bir liste gibi veri yapılarında depolayabilirler mi?</span><span class="sxs-lookup"><span data-stu-id="85f54-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="85f54-110">İşlev çağrısında bir işlevi bağımsız değişken olarak geçirebilir misiniz?</span><span class="sxs-lookup"><span data-stu-id="85f54-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="85f54-111">İşlev çağrısından bir işlev döndürebilir misiniz?</span><span class="sxs-lookup"><span data-stu-id="85f54-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="85f54-112">Son iki ölçü, *daha yüksek sıralı işlemler* veya *daha yüksek sıralı işlevler*olarak bilinenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85f54-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="85f54-113">Daha yüksek sıralı işlevler işlevleri bağımsız değişken olarak kabul eder ve işlev çağrılarının değeri olarak işlevleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="85f54-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="85f54-114">Bu işlemler, işlevleri eşleme işlevleri ve işlevlerinin oluşturulması gibi işlevsel programlamanın bu şekilde çalışmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="85f54-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="85f54-115">Değere bir ad verin</span><span class="sxs-lookup"><span data-stu-id="85f54-115">Give the Value a Name</span></span>

<span data-ttu-id="85f54-116">Bir işlev birinci sınıf bir değer ise, tam sayıları, dizeleri ve diğer yerleşik türleri de belirleyebilmeniz gibi, bu değeri de yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="85f54-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="85f54-117">Bu, bir tanımlayıcıyı bir değere bağlama gibi fonksiyonel programlama belgeleriyle ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="85f54-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="85f54-118">F # adları değerlere bağlamak için [ `let` bağlamaları](../language-reference/functions/let-bindings.md) kullanır: `let <identifier> = <value>` .</span><span class="sxs-lookup"><span data-stu-id="85f54-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="85f54-119">Aşağıdaki kodda iki örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85f54-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="85f54-120">Bir işlevi kolayca kolayca adlandırın.</span><span class="sxs-lookup"><span data-stu-id="85f54-120">You can name a function just as easily.</span></span> <span data-ttu-id="85f54-121">Aşağıdaki örnek, `squareIt` `squareIt` [lambda ifadesine](../language-reference/functions/lambda-expressions-the-fun-keyword.md) tanımlayıcıyı bağlayarak adlı bir işlevi tanımlar `fun n -> n * n` .</span><span class="sxs-lookup"><span data-stu-id="85f54-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="85f54-122">İşlevin `squareIt` tek bir parametresi vardır, `n` ve bu parametrenin karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="85f54-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="85f54-123">F #, daha az yazma ile aynı sonucu elde etmek için aşağıdaki daha kısa sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="85f54-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="85f54-124">Genellikle izleyen örnekler, `let <function-name> = <lambda-expression>` işlevlerin bildirimi ve diğer değer türlerinin bildirimi arasındaki benzerlikleri vurgulamak için ilk stili kullanır.</span><span class="sxs-lookup"><span data-stu-id="85f54-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="85f54-125">Ancak, tüm adlandırılmış işlevler kısa sözdizimi ile de yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="85f54-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="85f54-126">Örneklerden bazıları her iki şekilde yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="85f54-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="85f54-127">Değeri bir veri yapısında depolayın</span><span class="sxs-lookup"><span data-stu-id="85f54-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="85f54-128">Birinci sınıf bir değer, bir veri yapısında depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="85f54-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="85f54-129">Aşağıdaki kod, listelerde ve tanımlama değerlerinde değerleri depolayan örnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="85f54-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="85f54-130">Bir kayıt düzeninde depolanan bir işlev adının aslında bir işleve göre değerlendirileceğini doğrulamak için aşağıdaki örnek, `fst` ve `snd` işleçlerini kayıt kümesinden ilk ve ikinci öğeleri ayıklamak için kullanır `funAndArgTuple` .</span><span class="sxs-lookup"><span data-stu-id="85f54-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="85f54-131">Kayıt düzeni içindeki ilk öğe `squareIt` ve ikinci öğe `num` .</span><span class="sxs-lookup"><span data-stu-id="85f54-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="85f54-132">Tanımlayıcı, `num` işlev için geçerli bir bağımsız değişken olan tamsayı 10 ' a bir önceki örneğe bağlanır `squareIt` .</span><span class="sxs-lookup"><span data-stu-id="85f54-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="85f54-133">İkinci ifade, kayıt düzeni içindeki ilk öğeyi demet içindeki ikinci öğeye uygular: `squareIt num` .</span><span class="sxs-lookup"><span data-stu-id="85f54-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="85f54-134">Benzer şekilde, tanımlayıcı `num` ve tamsayı 10 ' da birbirinin yerine kullanılabilir, bu nedenle tanımlayıcı `squareIt` ve lambda ifadesi olabilir `fun n -> n * n` .</span><span class="sxs-lookup"><span data-stu-id="85f54-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="85f54-135">Değeri bağımsız değişken olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="85f54-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="85f54-136">Bir değerde bir dilde birinci sınıf durum varsa, bunu bir işleve bağımsız değişken olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="85f54-137">Örneğin, tamsayıların ve dizelerin bağımsız değişken olarak iletilmesi yaygındır.</span><span class="sxs-lookup"><span data-stu-id="85f54-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="85f54-138">Aşağıdaki kod, F # içinde bağımsız değişken olarak geçirilen tamsayıları ve dizeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="85f54-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="85f54-139">İşlevlerde birinci sınıf durum varsa, bunları aynı şekilde bağımsız değişken olarak geçirebilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="85f54-140">Bunun daha yüksek sıralı işlevlerin ilk özelliği olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="85f54-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="85f54-141">Aşağıdaki örnekte, işlevinin `applyIt` iki parametresi vardır `op` `arg` .</span><span class="sxs-lookup"><span data-stu-id="85f54-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="85f54-142">İçin bir parametresi ve işlevi için uygun bir bağımsız değişken içeren bir işlevde gönderirseniz `op` `arg` , işlevi uygulamanın sonucunu döndürür `op` `arg` .</span><span class="sxs-lookup"><span data-stu-id="85f54-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="85f54-143">Aşağıdaki örnekte, hem işlev bağımsız değişkeni hem de tamsayı bağımsız değişkeni, adları kullanılarak aynı şekilde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="85f54-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="85f54-144">Bir işlevi başka bir işleve bağımsız değişken olarak gönderebilme özelliği, eşleme veya filtre işlemleri gibi işlevsel programlama dillerinde ortak soyutlamaları daha da sağlar.</span><span class="sxs-lookup"><span data-stu-id="85f54-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="85f54-145">Örneğin, bir eşleme işlemi, bir liste içinde görüntülenen işlevler tarafından paylaşılan hesaplamayı yakalayan daha yüksek sıralı bir işlevdir, her öğe için bir şey yapın ve ardından sonuçların bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="85f54-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="85f54-146">Her bir öğeyi bir tamsayılar listesinde veya her öğenin kare halinde artırmak ya da dizeler listesindeki her öğeyi büyük harfe değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="85f54-147">Hesaplamanın hataya açık olan bölümü, listede ilerleyen özyinelemeli işlemdir ve döndürülecek sonuçların bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85f54-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="85f54-148">Bu bölüm, eşleme işlevinde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="85f54-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="85f54-149">Belirli bir uygulama için yazmanız gereken tek şey, her liste öğesine tek tek uygulamak istediğiniz işlevdir (ekleme, karelerini alıp, değişen Case).</span><span class="sxs-lookup"><span data-stu-id="85f54-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="85f54-150">Bu işlev, önceki örnekte olduğu gibi, eşleme işlevine bağımsız değişken olarak gönderilir `squareIt` `applyIt` .</span><span class="sxs-lookup"><span data-stu-id="85f54-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="85f54-151">F #, [listeler](../language-reference/lists.md), [diziler](../language-reference/arrays.md)ve [diziler](../language-reference/sequences.md)dahil olmak üzere çoğu koleksiyon türü için harita yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="85f54-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="85f54-152">Aşağıdaki örnekler listeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="85f54-152">The following examples use lists.</span></span> <span data-ttu-id="85f54-153">Söz dizimi `List.map <the function> <the list>` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="85f54-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="85f54-154">Daha fazla bilgi için bkz. [listeler](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="85f54-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="85f54-155">Işlev çağrısından değeri döndürün</span><span class="sxs-lookup"><span data-stu-id="85f54-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="85f54-156">Son olarak, bir işlevde bir dilde birinci sınıf durum varsa, tamsayılar ve dizeler gibi diğer türleri döndürmeniz gibi, bunu bir işlev çağrısının değeri olarak dönebilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="85f54-157">Aşağıdaki işlev çağrıları, tamsayılar döndürür ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85f54-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="85f54-158">Aşağıdaki işlev çağrısı bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="85f54-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="85f54-159">Satır içi olarak belirtilen aşağıdaki işlev çağrısı, bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="85f54-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="85f54-160">Görünen değer `True` .</span><span class="sxs-lookup"><span data-stu-id="85f54-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="85f54-161">İşlev çağrısının değeri olarak bir işlevi döndürme özelliği, daha yüksek sıralı işlevlerin ikinci özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="85f54-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="85f54-162">Aşağıdaki örnekte, `checkFor` bir bağımsız değişken alan bir işlev `item` olarak tanımlanır ve değeri olarak yeni bir işlev döndürür.</span><span class="sxs-lookup"><span data-stu-id="85f54-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="85f54-163">Döndürülen işlev, bağımsız değişkeni olarak bir liste alır `lst` ve içinde için arama yapar `item` `lst` .</span><span class="sxs-lookup"><span data-stu-id="85f54-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="85f54-164">Varsa `item` , işlev döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="85f54-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="85f54-165">Yoksa `item` , işlev döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="85f54-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="85f54-166">Önceki bölümde olduğu gibi, aşağıdaki kod, listede arama yapmak için [List. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists)bir belirtilen List işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="85f54-166">As in the previous section, the following code uses a provided list function, [List.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists), to search the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="85f54-167">Aşağıdaki kod, `checkFor` bir bağımsız değişkeni, bir listeyi alan ve listede 7 ' yi arayan yeni bir işlev oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="85f54-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="85f54-168">Aşağıdaki örnek, `compose` iki işlev bağımsız değişkeninin bir oluşumunu döndüren bir işlevi bildirmek Için F # içindeki işlevlerin ilk sınıf durumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="85f54-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> <span data-ttu-id="85f54-169">Daha da daha kısa bir sürüm için, "curried Işlevleri" başlıklı bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="85f54-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="85f54-170">Aşağıdaki kod, `compose` her ikisi de aynı türde tek bir bağımsız değişken alacak şekilde iki işlevi bağımsız değişken olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="85f54-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="85f54-171">Dönüş değeri, iki işlev bağımsız değişkeninin bileşimi olan yeni bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="85f54-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> <span data-ttu-id="85f54-172">F # iki işleç sağlar `<<` ve `>>` Bu işlev oluşturma işlevleri.</span><span class="sxs-lookup"><span data-stu-id="85f54-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="85f54-173">Örneğin, `let squareAndDouble2 = doubleIt << squareIt` önceki örnekteki ile eşdeğerdir `let squareAndDouble = compose doubleIt squareIt` .</span><span class="sxs-lookup"><span data-stu-id="85f54-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="85f54-174">İşlev çağrısının değeri olarak bir işlev döndürmesinin aşağıdaki örneği, basit bir tahmin oyunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85f54-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="85f54-175">Bir oyun oluşturmak için, `makeGame` birinin ' de tahmin etmesini istediğiniz değeri çağırın `target` .</span><span class="sxs-lookup"><span data-stu-id="85f54-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="85f54-176">İşlevden döndürülen değer bir `makeGame` bağımsız değişken (tahmin) alan ve tahminin doğru olup olmadığını raporlayan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="85f54-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="85f54-177">Aşağıdaki kod çağırır `makeGame` , için değeri gönderiliyor `7` `target` .</span><span class="sxs-lookup"><span data-stu-id="85f54-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="85f54-178">Tanımlayıcı, `playGame` döndürülen lambda ifadesine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="85f54-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="85f54-179">Bu nedenle, `playGame` için bir değer bağımsız değişkeni olarak alan bir işlevdir `guess` .</span><span class="sxs-lookup"><span data-stu-id="85f54-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="85f54-180">Curried Işlevleri</span><span class="sxs-lookup"><span data-stu-id="85f54-180">Curried Functions</span></span>

<span data-ttu-id="85f54-181">Önceki bölümde yer alan örneklerin birçoğu, F # işlev bildirimlerinde örtülü *currying* özelliğinden yararlanarak daha fazla öz yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="85f54-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="85f54-182">Currying, birden fazla parametresi olan bir işlevi, her birinin tek bir parametresi olan bir dizi katıştırılmış işlevlere dönüştüren bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="85f54-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="85f54-183">F # ' da, birden fazla parametresi olan işlevler kendiliğinden curried ' dir.</span><span class="sxs-lookup"><span data-stu-id="85f54-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="85f54-184">Örneğin, `compose` önceki bölümden üç parametre ile aşağıdaki kısa stilde gösterildiği gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="85f54-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="85f54-185">Ancak sonuç, içinde gösterildiği gibi, bir parametresinin bir işlevini döndüren tek bir parametre işlevi döndüren bir parametre işlevidir `compose4curried` .</span><span class="sxs-lookup"><span data-stu-id="85f54-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="85f54-186">Bu işleve çeşitli yollarla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-186">You can access this function in several ways.</span></span> <span data-ttu-id="85f54-187">Aşağıdaki örneklerin her biri döndürür ve 18 ' i görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85f54-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="85f54-188">`compose4`Örneklerden herhangi birinde ile değiştirebilirsiniz `compose4curried` .</span><span class="sxs-lookup"><span data-stu-id="85f54-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="85f54-189">İşlevin daha önce olduğu gibi hala çalıştığını doğrulamak için, özgün test çalışmalarını yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="85f54-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> <span data-ttu-id="85f54-190">Tanımlama grupları içindeki parametreleri kapsayan currying kısıtlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="85f54-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="85f54-191">Daha fazla bilgi için bkz. [parametrelerde ve bağımsız değişkenlerde](../language-reference/parameters-and-arguments.md)"parametre desenleri".</span><span class="sxs-lookup"><span data-stu-id="85f54-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="85f54-192">Aşağıdaki örnek, daha kısa bir sürümünü yazmak için örtülü currying kullanır `makeGame` .</span><span class="sxs-lookup"><span data-stu-id="85f54-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="85f54-193">Oluşturma `makeGame` ve işlevin nasıl döndürdüğü hakkında ayrıntılar `game` Bu biçimde daha az açık olur, ancak başlangıçtaki test çalışmalarını kullanarak sonucun aynı olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="85f54-194">Currying hakkında daha fazla bilgi için, bkz. [işlevlerde](../language-reference/functions/index.md)"bağımsız değişkenlerin kısmi uygulaması".</span><span class="sxs-lookup"><span data-stu-id="85f54-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="85f54-195">Tanımlayıcı ve Işlev tanımı değiştirilebilir</span><span class="sxs-lookup"><span data-stu-id="85f54-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="85f54-196">`num`Önceki örneklerde bulunan değişken adı 10 tamsayı olarak değerlendirilir ve bunun `num` geçerli olduğu, 10 ' un da geçerli olduğu bir işlem olmaz.</span><span class="sxs-lookup"><span data-stu-id="85f54-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="85f54-197">Aynı değer, işlev tanımlayıcılarının ve bunların değerlerinin her yerinde geçerlidir: işlevin adının her yerde kullanılabilmesi için, bağlandığı lambda ifadesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85f54-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="85f54-198">Aşağıdaki örnek `Boolean` adlı bir işlevi tanımlar `isNegative` ve sonra işlevin adını ve yerine işlevin tanımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="85f54-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="85f54-199">Sonraki üç örnek tüm döndürülür ve görüntülenir `False` .</span><span class="sxs-lookup"><span data-stu-id="85f54-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="85f54-200">Bir adım daha devam etmek için, için `applyIt` öğesine bağlanan değeri değiştirin `applyIt` .</span><span class="sxs-lookup"><span data-stu-id="85f54-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="85f54-201">İşlevler F içindeki Ilk sınıf değerlerdir\#</span><span class="sxs-lookup"><span data-stu-id="85f54-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="85f54-202">Önceki bölümlerde yer alan örneklerde, F # içindeki işlevlerin F # ' ta birinci sınıf değerler olması için kriterleri karşılamakta olduğu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="85f54-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="85f54-203">Bir tanımlayıcıyı işlev tanımına bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="85f54-204">Bir işlevi bir veri yapısında saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="85f54-205">Bir işlevi bağımsız değişken olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="85f54-206">İşlev çağrısının değeri olarak bir işlev döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85f54-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="85f54-207">F # hakkında daha fazla bilgi için [f # dil başvurusuna](../language-reference/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="85f54-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="85f54-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="85f54-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="85f54-209">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85f54-209">Description</span></span>

<span data-ttu-id="85f54-210">Aşağıdaki kod, bu konudaki tüm örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="85f54-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="85f54-211">Kod</span><span class="sxs-lookup"><span data-stu-id="85f54-211">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="85f54-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85f54-212">See also</span></span>

- [<span data-ttu-id="85f54-213">Listeler</span><span class="sxs-lookup"><span data-stu-id="85f54-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="85f54-214">Tanımlama grupları</span><span class="sxs-lookup"><span data-stu-id="85f54-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="85f54-215">İşlevler</span><span class="sxs-lookup"><span data-stu-id="85f54-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="85f54-216">`let` Lara</span><span class="sxs-lookup"><span data-stu-id="85f54-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="85f54-217">Lambda Ifadeleri: `fun` anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="85f54-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
