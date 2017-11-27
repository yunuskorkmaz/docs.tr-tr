---
title: "Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="6951f-102">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6951f-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="6951f-103">Çağırdığınızda bir `Sub` veya `Function` yordam bağımsız değişkenleri iletebilir *konuma göre* — yordam tanımında göründükleri sırada — veya bunları geçirebilirsiniz *ada göre*, olmadan konumlandırmak için şekilde.</span><span class="sxs-lookup"><span data-stu-id="6951f-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="6951f-104">Ada göre bir bağımsız değişken geçirdiğinizde, bağımsız değişken adını ardından bir iki nokta üst üste ve eşittir işareti tarafından bildirilen belirtin (`:=`), ardından bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="6951f-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="6951f-105">Adlandırılmış bağımsız değişkenler herhangi bir sırada sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6951f-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="6951f-106">Örneğin, aşağıdaki `Sub` yordamın kullandığı üç bağımsız değişken:</span><span class="sxs-lookup"><span data-stu-id="6951f-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 <span data-ttu-id="6951f-107">Bu yordam çağrısı, konum, ad veya her ikisinin bir karışımıyla kullanarak bağımsız değişkenleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6951f-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="6951f-108">Konuma göre bağımsız değişkenleri geçirme</span><span class="sxs-lookup"><span data-stu-id="6951f-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="6951f-109">Yordam çağrısı `studentInfo` konuma göre geçirilen ve aşağıdaki örnekte gösterildiği gibi virgülle ayrılmış bağımsız değişkenlerini:</span><span class="sxs-lookup"><span data-stu-id="6951f-109">You can call the procedure `studentInfo` with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 <span data-ttu-id="6951f-110">İsteğe bağlı bir bağımsız değişken konumsal bağımsız değişken listesinde atlarsanız, onun yerine virgül ile tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6951f-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="6951f-111">Aşağıdaki örnek çağrıları `studentInfo` olmadan `age` bağımsız değişkeni:</span><span class="sxs-lookup"><span data-stu-id="6951f-111">The following example calls `studentInfo` without the `age` argument:</span></span>  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="6951f-112">Ada göre bağımsız değişkenleri geçirme</span><span class="sxs-lookup"><span data-stu-id="6951f-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="6951f-113">Alternatif olarak, çağırabilirsiniz `studentInfo` adıyla geçirilen bağımsız değişkenlerle aşağıdaki örnekte gösterildiği gibi virgülle ayrıca sınırlandırılmış:</span><span class="sxs-lookup"><span data-stu-id="6951f-113">Alternatively, you can call `studentInfo` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="6951f-114">Bağımsız değişkenleri konuma ve ada göre bir arada kullanma</span><span class="sxs-lookup"><span data-stu-id="6951f-114">Mixing Arguments by Position and by Name</span></span>  
 <span data-ttu-id="6951f-115">Aşağıdaki örnekte gösterildiği gibi değişkenleri hem konuma ve ada göre tek bir yordam çağrısında sağlayabilir:</span><span class="sxs-lookup"><span data-stu-id="6951f-115">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 <span data-ttu-id="6951f-116">Önceki örnekte, hiçbir ek virgülle belirtilmemişse yerini tutmak için gerekli `age` bağımsız değişkeni, bu yana `birth` adıyla geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6951f-116">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
 <span data-ttu-id="6951f-117">Bağımsız değişkenler bir karışımını konumunu ve adını, konumsal bağımsız değişkenler sağladığında tüm ilk gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="6951f-117">When you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="6951f-118">Ada göre bağımsız değişken sağlayın sonra kalan bağımsız değişkenleri tüm ada göre olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6951f-118">Once you supply an argument by name, the remaining arguments must all be by name.</span></span>  
  
## <a name="supplying-optional-arguments-by-name"></a><span data-ttu-id="6951f-119">Ada göre isteğe bağlı bağımsız değişkenler sağlama</span><span class="sxs-lookup"><span data-stu-id="6951f-119">Supplying Optional Arguments by Name</span></span>  
 <span data-ttu-id="6951f-120">Birden fazla isteğe bağlı bağımsız değişkeni olan bir yordam çağırma bağımsız değişkenleri ada göre geçirme özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6951f-120">Passing arguments by name is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="6951f-121">Ada göre bağımsız değişken sağlarsanız, konumsal bağımsız değişkenler eksik belirtmek için ardışık virgül kullanmak zorunda değil.</span><span class="sxs-lookup"><span data-stu-id="6951f-121">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="6951f-122">Ada göre bağımsız değişkenleri geçirme Ayrıca, geçirme ve hangilerinin atlama hangi bağımsız değişkenleri izlemek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6951f-122">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="6951f-123">Bağımsız değişken adı tarafından sağladığını kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="6951f-123">Restrictions on Supplying Arguments by Name</span></span>  
 <span data-ttu-id="6951f-124">Gerekli bağımsız girmekten kaçının adıyla bağımsız değişkenlerini geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6951f-124">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="6951f-125">İsteğe bağlı bağımsız değişkenler atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6951f-125">You can omit only the optional arguments.</span></span>  
  
 <span data-ttu-id="6951f-126">Ada göre parametre dizisi geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6951f-126">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="6951f-127">Bu yordam çağrısı, belirsiz sayıda parametre dizisi için virgülle ayrılmış bağımsız değişkenleri sağlayın ve derleyici birden fazla bağımsız değişken tek bir adla ilişkilendiremezsiniz kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="6951f-127">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6951f-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6951f-128">See Also</span></span>  
 [<span data-ttu-id="6951f-129">Yordamları</span><span class="sxs-lookup"><span data-stu-id="6951f-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="6951f-130">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6951f-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="6951f-131">Nasıl yapılır: bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="6951f-131">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="6951f-132">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="6951f-132">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="6951f-133">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="6951f-133">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="6951f-134">Parametre dizileri</span><span class="sxs-lookup"><span data-stu-id="6951f-134">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="6951f-135">İsteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="6951f-135">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="6951f-136">ParamArray</span><span class="sxs-lookup"><span data-stu-id="6951f-136">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
