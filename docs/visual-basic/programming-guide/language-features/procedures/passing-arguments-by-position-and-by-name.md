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
ms.openlocfilehash: 686b64977f086c8128e56298a0ed8c5aa0c51efa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364038"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="f3e5c-102">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3e5c-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="f3e5c-103">Bir `Sub` veya `Function` yordamını çağırdığınızda, bağımsız değişkenleri, yordamın tanımında göründükleri sırada, *konuma göre* geçirebilirsiniz veya konuma *göre onları ada göre*geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="f3e5c-104">Bir bağımsız değişkeni adına göre geçirdiğinizde, bağımsız değişkenin belirtilen adını, ardından iki nokta üst üste ve eşittir işaretini ( `:=` ) ve ardından bağımsız değişken değerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="f3e5c-105">Adlandırılmış bağımsız değişkenleri istediğiniz sırada sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="f3e5c-106">Örneğin, aşağıdaki `Sub` yordam üç bağımsız değişken alır:</span><span class="sxs-lookup"><span data-stu-id="f3e5c-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="f3e5c-107">Bu yordamı çağırdığınızda, bağımsız değişkenleri konuma, ada veya her ikisinin bir karışımını kullanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="f3e5c-108">Bağımsız değişkenleri konuma göre geçirme</span><span class="sxs-lookup"><span data-stu-id="f3e5c-108">Passing Arguments by Position</span></span>

<span data-ttu-id="f3e5c-109">`Display`Aşağıdaki örnekte gösterildiği gibi, konum ile geçirilen bağımsız değişkenlerle yöntemi, virgülle ayrılmış şekilde çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3e5c-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="f3e5c-110">Konumsal bağımsız değişken listesinde isteğe bağlı bir bağımsız değişkeni atlarsanız, onun yerini virgül ile tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="f3e5c-111">Aşağıdaki örnek `Display` yöntemi `age` bağımsız değişken olmadan çağırır:</span><span class="sxs-lookup"><span data-stu-id="f3e5c-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="f3e5c-112">Bağımsız değişkenleri ada göre geçirme</span><span class="sxs-lookup"><span data-stu-id="f3e5c-112">Passing Arguments by Name</span></span>

<span data-ttu-id="f3e5c-113">Alternatif olarak, `Display` Aşağıdaki örnekte gösterildiği gibi virgülle ayrılmış şekilde, ada göre geçirilen bağımsız değişkenlerle de çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3e5c-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="f3e5c-114">Bu şekilde bağımsız değişkenleri bu şekilde geçirmek, birden fazla isteğe bağlı bağımsız değişkeni olan bir yordamı çağırdığınızda özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="f3e5c-115">Ada göre bağımsız değişkenler sağlarsanız, eksik Konumsal bağımsız değişkenleri belirtmek için ardışık virgüller kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="f3e5c-116">Bağımsız değişkenleri ada göre geçirmek, geçirdiğiniz bağımsız değişkenleri ve hangilerinin dışarıda geçtiğini izlemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="f3e5c-117">Bağımsız değişkenleri konuma ve ada göre karıştırma</span><span class="sxs-lookup"><span data-stu-id="f3e5c-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="f3e5c-118">Aşağıdaki örnekte gösterildiği gibi tek bir yordam çağrısında hem konuma hem de ada göre bağımsız değişkenler sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3e5c-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="f3e5c-119">Yukarıdaki örnekte, atlanan bağımsız değişkenin yerini tutmak için ek virgül gerekmez `age` , çünkü `birth` ad ile geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="f3e5c-120">15,5 ' den önceki Visual Basic sürümlerinde, konum ve ad karışımı ile bağımsız değişkenleri sağlarsanız, Konumsal bağımsız değişkenlerin hepsi ilk olarak gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="f3e5c-121">Ada göre bir bağımsız değişken sağlarsanız, kalan tüm bağımsız değişkenlerin tümünün adına göre geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="f3e5c-122">Örneğin, aşağıdaki `Display` Yöntem çağrısı derleyici hatası [BC30241: adlandırılmış bağımsız değişken bekleniyor](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="f3e5c-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="f3e5c-123">Visual Basic 15,5 ' den başlayarak, konum bağımsız değişkenleri bitiş Konumsal bağımsız değişkenleri doğru konumundayken adlandırılmış bağımsız değişkenler izleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="f3e5c-124">Visual Basic 15,5 altında derlenirse, yönteme yapılan önceki çağrı `Display` başarıyla derlenir ve artık derleyici hatası [BC30241](../../../misc/bc30241.md)oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="f3e5c-125">Adlandırılmış ve Konumsal bağımsız değişkenleri herhangi bir sırada karıştırabilme ve eşleştirme özelliği, kodunuzun daha okunaklı olması için adlandırılmış bir bağımsız değişken kullanmak istediğinizde özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="f3e5c-126">Örneğin, aşağıdaki `Person` sınıf oluşturucusu türünde iki bağımsız değişken gerektirir `Person` , ikisi de olabilir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="f3e5c-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="f3e5c-127">Karışık adlandırılmış ve Konumsal bağımsız değişkenlerin kullanılması, `father` ve bağımsız değişkenlerinin değeri olduğunda kod hedefini açık hale getirmek için yardımcı olur `mother` `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="f3e5c-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="f3e5c-128">Adlandırılmış bağımsız değişkenlerle Konumsal bağımsız değişkenleri izlemek için, Visual Basic projesi ( \* . vbproj) dosyanıza aşağıdaki öğeyi eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="f3e5c-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="f3e5c-129">Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="f3e5c-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="f3e5c-130">Ada göre bağımsız değişken sağlamaya yönelik kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="f3e5c-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="f3e5c-131">Gerekli bağımsız değişkenleri girmekten kaçınmak için bağımsız değişkenleri ada göre geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="f3e5c-132">Yalnızca isteğe bağlı bağımsız değişkenleri atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="f3e5c-133">Bir parametre dizisini ada göre geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="f3e5c-134">Bunun nedeni, yordamı çağırdığınızda parametre dizisi için sınırsız sayıda virgülle ayrılmış bağımsız değişken sağlarsınız ve derleyici birden fazla bağımsız değişkeni tek bir adla ilişkilendiremez.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3e5c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3e5c-135">See also</span></span>

- [<span data-ttu-id="f3e5c-136">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f3e5c-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f3e5c-137">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f3e5c-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f3e5c-138">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="f3e5c-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="f3e5c-139">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="f3e5c-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="f3e5c-140">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3e5c-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="f3e5c-141">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="f3e5c-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="f3e5c-142">İsteğe Bağlı</span><span class="sxs-lookup"><span data-stu-id="f3e5c-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="f3e5c-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="f3e5c-143">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
