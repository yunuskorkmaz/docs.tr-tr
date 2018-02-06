---
title: "Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)"
ms.custom: 
ms.date: 02/01/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13f5e5a8da6a899d4920a25b250ca88b2a21f559
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="b5132-102">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5132-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="b5132-103">Çağırdığınızda bir `Sub` veya `Function` yordam bağımsız değişkenleri iletebilir *konuma göre* — yordam tanımında göründükleri sırada — veya bunları geçirebilirsiniz *ada göre*, olmadan konumlandırmak için şekilde.</span><span class="sxs-lookup"><span data-stu-id="b5132-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="b5132-104">Ada göre bir bağımsız değişken geçirdiğinizde, bağımsız değişken adını ardından bir iki nokta üst üste ve eşittir işareti tarafından bildirilen belirtin (`:=`), ardından bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="b5132-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="b5132-105">Adlandırılmış bağımsız değişkenler herhangi bir sırada sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b5132-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="b5132-106">Örneğin, aşağıdaki `Sub` yordamın kullandığı üç bağımsız değişken:</span><span class="sxs-lookup"><span data-stu-id="b5132-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 <span data-ttu-id="b5132-107">Bu yordam çağrısı, konum, ad veya her ikisinin bir karışımıyla kullanarak bağımsız değişkenleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5132-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="b5132-108">Konuma göre bağımsız değişkenleri geçirme</span><span class="sxs-lookup"><span data-stu-id="b5132-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="b5132-109">Çağırabilirsiniz `Display` değişkenlerinin yöntemiyle konuma göre geçirilen ve aşağıdaki örnekte gösterildiği gibi virgülle ayrılmış:</span><span class="sxs-lookup"><span data-stu-id="b5132-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 <span data-ttu-id="b5132-110">İsteğe bağlı bir bağımsız değişken konumsal bağımsız değişken listesinde atlarsanız, onun yerine virgül ile tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5132-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="b5132-111">Aşağıdaki örnek çağrıları `Display` yöntemi olmadan `age` bağımsız değişkeni:</span><span class="sxs-lookup"><span data-stu-id="b5132-111">The following example calls the `Display` method without the `age` argument:</span></span>  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="b5132-112">Ada göre bağımsız değişkenleri geçirme</span><span class="sxs-lookup"><span data-stu-id="b5132-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="b5132-113">Alternatif olarak, çağırabilirsiniz `Display` adıyla geçirilen bağımsız değişkenlerle aşağıdaki örnekte gösterildiği gibi virgülle ayrıca sınırlandırılmış:</span><span class="sxs-lookup"><span data-stu-id="b5132-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 <span data-ttu-id="b5132-114">Birden fazla isteğe bağlı bağımsız değişkeni olan bir yordam çağırma bu şekilde adıyla bağımsız değişkenleri geçirme özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5132-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="b5132-115">Ada göre bağımsız değişken sağlarsanız, konumsal bağımsız değişkenler eksik belirtmek için ardışık virgül kullanmak zorunda değil.</span><span class="sxs-lookup"><span data-stu-id="b5132-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="b5132-116">Ada göre bağımsız değişkenleri geçirme Ayrıca, geçirme ve hangilerinin atlama hangi bağımsız değişkenleri izlemek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b5132-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="b5132-117">Bağımsız değişkenleri konuma ve ada göre bir arada kullanma</span><span class="sxs-lookup"><span data-stu-id="b5132-117">Mixing Arguments by Position and by Name</span></span>  

<span data-ttu-id="b5132-118">Aşağıdaki örnekte gösterildiği gibi değişkenleri hem konuma ve ada göre tek bir yordam çağrısında sağlayabilir:</span><span class="sxs-lookup"><span data-stu-id="b5132-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 <span data-ttu-id="b5132-119">Önceki örnekte, hiçbir ek virgülle belirtilmemişse yerini tutmak için gerekli `age` bağımsız değişkeni, bu yana `birth` adıyla geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b5132-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
<span data-ttu-id="b5132-120">Bağımsız değişkenler bir karışımını konumunu ve adını, konumsal bağımsız değişkenler sağladığında sürümlerinde Visual Basic 15,5 önce tüm ilk gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="b5132-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="b5132-121">Ada göre bağımsız değişken sağlayın sonra kalan tüm bağımsız değişkenleri tüm adıyla geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="b5132-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="b5132-122">Örneğin, için aşağıdaki çağrı `Display` yöntemi görüntüler derleyici hatası [BC30241: adlandırılmış bağımsız değişkeni beklenen](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="b5132-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

<span data-ttu-id="b5132-123">Visual Basic 15,5 ile başlayarak, bitiş konumsal bağımsız değişkenlerin doğru konumda ise konumsal bağımsız değişkenleri adlandırılmış bağımsız değişkenler izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5132-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="b5132-124">Visual Basic 15,5, önceki çağrısı altında derlenmiş ise `Display` yöntemi başarıyla derlenir ve artık derleyici hatası oluşturur [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="b5132-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>  

<span data-ttu-id="b5132-125">Karışık ve herhangi bir sırada adlandırılmış ve konumsal bağımsız değişkenler eşleştirmek için bu özelliği kodunuzu daha okunabilir hale getirmek için bir adlandırılmış bağımsız değişkeni kullanmak istediğinizde özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5132-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="b5132-126">Örneğin, aşağıdaki `Person` sınıfı oluşturucusu türünde iki bağımsız değişken gerektirir `Person`, her ikisi de olabilir `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b5132-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span> 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

<span data-ttu-id="b5132-127">Clear kodu amacı olmasına yardımcı olur, karma adlandırılmış ve konumsal bağımsız değişkenler kullanarak değerini `father` ve `mother` bağımsız değişkenleri olan `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="b5132-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

<span data-ttu-id="b5132-128">Adlandırılmış bağımsız değişkenler konumsal değişkenleriyle izlemek için aşağıdaki öğeyi Visual Basic projenize eklemeniz gerekir (\*.vbproj) dosyası:</span><span class="sxs-lookup"><span data-stu-id="b5132-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="b5132-129">Bağımsız değişken adı tarafından sağladığını kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="b5132-129">Restrictions on Supplying Arguments by Name</span></span>  

<span data-ttu-id="b5132-130">Gerekli bağımsız girmekten kaçının adıyla bağımsız değişkenlerini geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5132-130">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="b5132-131">İsteğe bağlı bağımsız değişkenler atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5132-131">You can omit only the optional arguments.</span></span>  
  
<span data-ttu-id="b5132-132">Ada göre parametre dizisi geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5132-132">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="b5132-133">Bu yordam çağrısı, belirsiz sayıda parametre dizisi için virgülle ayrılmış bağımsız değişkenleri sağlayın ve derleyici birden fazla bağımsız değişken tek bir adla ilişkilendiremezsiniz kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="b5132-133">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5132-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5132-134">See Also</span></span>  
 [<span data-ttu-id="b5132-135">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b5132-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="b5132-136">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="b5132-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b5132-137">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="b5132-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="b5132-138">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="b5132-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="b5132-139">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5132-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="b5132-140">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="b5132-140">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="b5132-141">Optional</span><span class="sxs-lookup"><span data-stu-id="b5132-141">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="b5132-142">ParamArray</span><span class="sxs-lookup"><span data-stu-id="b5132-142">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
