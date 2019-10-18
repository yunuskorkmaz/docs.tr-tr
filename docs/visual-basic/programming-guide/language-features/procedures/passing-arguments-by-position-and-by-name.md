---
title: Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)
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
ms.openlocfilehash: 2fa07a4ecf31b9dc0fee91593e793f3b00c5a83b
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524440"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="d7361-102">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7361-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="d7361-103">Bir `Sub` veya `Function` yordamını çağırdığınızda, bağımsız değişkenleri, yordamın tanımında göründükleri *sırada — ya* da *konuma göre geçirebilirsiniz, sonra*da konuma göre geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7361-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="d7361-104">Bir bağımsız değişkeni adına göre geçirdiğinizde, bağımsız değişkenin belirtilen adını, ardından iki nokta üst üste ve eşittir işaretini (`:=`) ve ardından bağımsız değişken değerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7361-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="d7361-105">Adlandırılmış bağımsız değişkenleri istediğiniz sırada sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7361-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="d7361-106">Örneğin, aşağıdaki `Sub` yordamı üç bağımsız değişkeni alır:</span><span class="sxs-lookup"><span data-stu-id="d7361-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="d7361-107">Bu yordamı çağırdığınızda, bağımsız değişkenleri konuma, ada veya her ikisinin bir karışımını kullanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7361-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="d7361-108">Bağımsız değişkenleri konuma göre geçirme</span><span class="sxs-lookup"><span data-stu-id="d7361-108">Passing Arguments by Position</span></span>

<span data-ttu-id="d7361-109">Aşağıdaki örnekte gösterildiği gibi, konum ve virgülle ayrılmış bağımsız değişkenleriyle `Display` yöntemi çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d7361-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="d7361-110">Konumsal bağımsız değişken listesinde isteğe bağlı bir bağımsız değişkeni atlarsanız, onun yerini virgül ile tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7361-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="d7361-111">Aşağıdaki örnek, `age` bağımsız değişkeni olmadan `Display` yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="d7361-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="d7361-112">Bağımsız değişkenleri ada göre geçirme</span><span class="sxs-lookup"><span data-stu-id="d7361-112">Passing Arguments by Name</span></span>

<span data-ttu-id="d7361-113">Alternatif olarak, aşağıdaki örnekte gösterildiği gibi, ada göre geçirilen bağımsız değişkenlerle `Display` çağırabilirsiniz ve virgülle da ayrılır:</span><span class="sxs-lookup"><span data-stu-id="d7361-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="d7361-114">Bu şekilde bağımsız değişkenleri bu şekilde geçirmek, birden fazla isteğe bağlı bağımsız değişkeni olan bir yordamı çağırdığınızda özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d7361-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="d7361-115">Ada göre bağımsız değişkenler sağlarsanız, eksik Konumsal bağımsız değişkenleri belirtmek için ardışık virgüller kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d7361-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="d7361-116">Bağımsız değişkenleri ada göre geçirmek, geçirdiğiniz bağımsız değişkenleri ve hangilerinin dışarıda geçtiğini izlemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d7361-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="d7361-117">Bağımsız değişkenleri konuma ve ada göre karıştırma</span><span class="sxs-lookup"><span data-stu-id="d7361-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="d7361-118">Aşağıdaki örnekte gösterildiği gibi tek bir yordam çağrısında hem konuma hem de ada göre bağımsız değişkenler sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d7361-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="d7361-119">Yukarıdaki örnekte, `birth` adı ile geçirildiğinden atlanan `age` bağımsız değişkeninin yerini tutmak için ek virgül gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d7361-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="d7361-120">15,5 ' den önceki Visual Basic sürümlerinde, konum ve ad karışımı ile bağımsız değişkenleri sağlarsanız, Konumsal bağımsız değişkenlerin hepsi ilk olarak gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="d7361-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="d7361-121">Ada göre bir bağımsız değişken sağlarsanız, kalan tüm bağımsız değişkenlerin tümünün adına göre geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7361-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="d7361-122">Örneğin, `Display` yöntemine yapılan aşağıdaki çağrı derleyici hatası [BC30241: adlandırılmış bağımsız değişken bekleniyor](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="d7361-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="d7361-123">Visual Basic 15,5 ' den başlayarak, konum bağımsız değişkenleri bitiş Konumsal bağımsız değişkenleri doğru konumundayken adlandırılmış bağımsız değişkenler izleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d7361-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="d7361-124">Visual Basic 15,5 altında derlenirse, `Display` yöntemine yapılan önceki çağrı başarıyla derlenir ve artık derleyici hatası [BC30241](../../../misc/bc30241.md)oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d7361-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="d7361-125">Adlandırılmış ve Konumsal bağımsız değişkenleri herhangi bir sırada karıştırabilme ve eşleştirme özelliği, kodunuzun daha okunaklı olması için adlandırılmış bir bağımsız değişken kullanmak istediğinizde özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d7361-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="d7361-126">Örneğin, aşağıdaki `Person` sınıf oluşturucusu `Person` türünde iki bağımsız değişken gerektirir, ikisi de `Nothing` olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7361-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="d7361-127">Karışık adlandırılmış ve Konumsal bağımsız değişkenlerin kullanılması, `father` ve `mother` bağımsız değişkenlerin değeri `Nothing` olduğunda kodun amacını açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d7361-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="d7361-128">Adlandırılmış bağımsız değişkenlerle Konumsal bağımsız değişkenleri izlemek için, Visual Basic projesi (\*. vbproj) dosyanıza aşağıdaki öğeyi eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="d7361-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="d7361-129">Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="d7361-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="d7361-130">Ada göre bağımsız değişken sağlamaya yönelik kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="d7361-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="d7361-131">Gerekli bağımsız değişkenleri girmekten kaçınmak için bağımsız değişkenleri ada göre geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7361-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="d7361-132">Yalnızca isteğe bağlı bağımsız değişkenleri atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7361-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="d7361-133">Bir parametre dizisini ada göre geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7361-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="d7361-134">Bunun nedeni, yordamı çağırdığınızda parametre dizisi için sınırsız sayıda virgülle ayrılmış bağımsız değişken sağlarsınız ve derleyici birden fazla bağımsız değişkeni tek bir adla ilişkilendiremez.</span><span class="sxs-lookup"><span data-stu-id="d7361-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7361-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7361-135">See also</span></span>

- [<span data-ttu-id="d7361-136">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d7361-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d7361-137">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="d7361-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d7361-138">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="d7361-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="d7361-139">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="d7361-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d7361-140">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7361-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="d7361-141">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="d7361-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="d7361-142">Optional</span><span class="sxs-lookup"><span data-stu-id="d7361-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="d7361-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="d7361-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
