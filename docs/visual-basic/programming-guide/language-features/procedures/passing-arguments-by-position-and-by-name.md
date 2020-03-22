---
title: Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400857"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="79644-102">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79644-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="79644-103">Bir `Sub` `Function` yordamı aradiğinizde, bağımsız değişkenleri yordamın tanımında göründükleri sırayla konuma *göre* geçirebilir veya konuma bakılmaksızın bunları *adlarına*göre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79644-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="79644-104">Bir bağımsız değişkeni ada göre geçtiğizde, bağımsız değişkenin beyan edilen`:=`adını ve ardından bir iki nokta üst üste ve eşit bir işaret (), ardından bağımsız değişken değerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79644-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="79644-105">Adlandırılmış bağımsız değişkenleri istediğiniz sırada sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79644-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="79644-106">Örneğin, aşağıdaki `Sub` yordam üç bağımsız değişken alır:</span><span class="sxs-lookup"><span data-stu-id="79644-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="79644-107">Bu yordamı çağırdığınızda, bağımsız değişkenleri konuma, ada göre veya her ikisinin karışımını kullanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79644-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="79644-108">Bağımsız Değişkenleri Konuma Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="79644-108">Passing Arguments by Position</span></span>

<span data-ttu-id="79644-109">`Display` Aşağıdaki örnekte gösterildiği gibi, konuma göre geçirilen ve virgülle sınırlandırılabilen bağımsız değişkenleriyle yöntemi çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="79644-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="79644-110">Konumsal bağımsız değişken listesinde isteğe bağlı bir bağımsız değişkeni atlarsanız, virgülle yerini tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="79644-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="79644-111">Aşağıdaki `age` örnek, `Display` bağımsız değişken olmadan yöntemi çağırır:</span><span class="sxs-lookup"><span data-stu-id="79644-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="79644-112">Bağımsız Değişkenleri Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="79644-112">Passing Arguments by Name</span></span>

<span data-ttu-id="79644-113">Alternatif olarak, aşağıdaki `Display` örnekte gösterildiği gibi, ad ile geçirilen ve virgülle de sınırlandırılmış bağımsız değişkenleri arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="79644-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="79644-114">Bağımsız değişkenleri bu şekilde ada göre geçirme, özellikle birden fazla isteğe bağlı bağımsız değişkeni olan bir yordamı çağırdığınızda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="79644-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="79644-115">Bağımsız değişkenleri ada göre sağlıyorsanız, eksik konumsal bağımsız değişkenleri belirtmek için ardışık virgül kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="79644-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="79644-116">Bağımsız değişkenleri ada göre aktarmak, hangi bağımsız değişkenleri geçtiğinizü ve hangilerini atladığınızı izlemeyi de kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="79644-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="79644-117">Konum ve Ada Göre Bağımsız Değişkenleri Karıştırma</span><span class="sxs-lookup"><span data-stu-id="79644-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="79644-118">Aşağıdaki örnekte gösterildiği gibi, bağımsız değişkenleri tek bir yordam çağrısında hem konuma hem de ada göre sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="79644-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="79644-119">Önceki örnekte, atlanan `age` bağımsız değişkenin yerini tutmak için fazladan virgül `birth` gerekmez, çünkü ada geçilir.</span><span class="sxs-lookup"><span data-stu-id="79644-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="79644-120">Visual Basic'in 15.5'ten önceki sürümlerinde, konum ve ad karışımıyla bağımsız değişkenler sağladığınızda, konumsal bağımsız değişkenlerin tümü önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="79644-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="79644-121">Bir bağımsız değişkeni ada göre tedarik ettikten sonra, kalan bağımsız değişkenlerden herhangi bir inanca göre geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="79644-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="79644-122">Örneğin, `Display` yönteme aşağıdaki çağrı derleyici hata [BC30241 görüntüler: Adlandırılmış bağımsız değişken bekleniyor](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="79644-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="79644-123">Visual Basic 15.5 ile başlayarak, bitiş konumsal bağımsız değişkenleri doğru konumdaysa, konumsal bağımsız değişkenler adlandırılmış bağımsız değişkenleri izleyebilir.</span><span class="sxs-lookup"><span data-stu-id="79644-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="79644-124">Visual Basic 15.5 altında derlenirse, `Display` yönteme yapılan önceki çağrı başarılı bir şekilde derlenir ve artık derleme hatası [OLUŞTURMAYAN BC30241.](../../../misc/bc30241.md)</span><span class="sxs-lookup"><span data-stu-id="79644-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="79644-125">Adı geçen ve konumlandırılmış bağımsız değişkenleri herhangi bir sırada karıştırma ve eşleştirme yeteneği, kodunuzu daha okunabilir hale getirmek için adlandırılmış bir bağımsız değişken kullanmak istediğinizde özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="79644-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="79644-126">Örneğin, aşağıdaki `Person` sınıf oluşturucu türünde `Person`iki bağımsız değişken `Nothing`gerektirir , her ikisi de olabilir .</span><span class="sxs-lookup"><span data-stu-id="79644-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="79644-127">Karışık adlandırılmış ve konumsal bağımsız değişkenler kullanarak kodun amacı `father` `mother` ve `Nothing`bağımsız değişkenlerin değeri açık hale getirmeye yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="79644-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="79644-128">Adlandırılmış bağımsız değişkenlerle konumsal bağımsız değişkenleri izlemek için Visual\*Basic projenize (.vbproj) aşağıdaki öğeyi eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="79644-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="79644-129">Daha fazla bilgi için [Visual Basic dil sürümünü ayarlama ya](../../../language-reference/configure-language-version.md)da bkz.</span><span class="sxs-lookup"><span data-stu-id="79644-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="79644-130">Ada Göre Bağımsız Değişken Sağlama Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="79644-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="79644-131">Gerekli bağımsız değişkenleri girmemek için bağımsız değişkenleri adıyla geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="79644-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="79644-132">Yalnızca isteğe bağlı bağımsız değişkenleri atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79644-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="79644-133">Bir parametre dizini ada göre geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="79644-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="79644-134">Bunun nedeni, yordamı çağırdığınızda, parametre dizisi için belirsiz sayıda virgülle ayrılmış bağımsız değişken sağlamanızdır ve derleyici birden fazla bağımsız değişkeni tek bir adla ilişkilendiremez.</span><span class="sxs-lookup"><span data-stu-id="79644-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="79644-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79644-135">See also</span></span>

- [<span data-ttu-id="79644-136">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="79644-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="79644-137">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="79644-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="79644-138">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="79644-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="79644-139">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="79644-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="79644-140">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="79644-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="79644-141">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="79644-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="79644-142">Isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="79644-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="79644-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="79644-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
