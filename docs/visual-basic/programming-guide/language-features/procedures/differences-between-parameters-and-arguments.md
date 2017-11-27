---
title: "Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="73c23-102">Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73c23-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="73c23-103">Çoğu durumda, bir yordam, onu çağrıldı koşullar hakkında bazı bilgileri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73c23-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="73c23-104">Yinelenen veya paylaşılan görevleri gerçekleştiren bir yordam her çağrı için farklı bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="73c23-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="73c23-105">Bu bilgiler değişkenlerinin, sabitleri ve onu çağırdığınızda, yordama geçirdiğiniz ifadeler oluşur.</span><span class="sxs-lookup"><span data-stu-id="73c23-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="73c23-106">Bu bilgileri yordam için iletişim kurmak için yordamı tanımlayan bir *parametresi*, ve çağrıyı yapan kod geçirir bir *bağımsız değişkeni* parametreye.</span><span class="sxs-lookup"><span data-stu-id="73c23-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="73c23-107">Park alanı parametre ve bağımsız değişken bir otomobil olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73c23-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="73c23-108">Yalnızca farklı otomobiller bir park alanında farklı zamanlarda park olarak çağıran kodu, BT'nin yordam çağrıları her zaman aynı parametresi için farklı bir bağımsız değişken geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73c23-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="73c23-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73c23-109">Parameters</span></span>  
 <span data-ttu-id="73c23-110">A *parametresi* yordamı, çağırdığınızda geçirmeniz bekliyor bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73c23-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="73c23-111">Yordam bildirimi parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73c23-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="73c23-112">Tanımladığınızda bir `Function` veya `Sub` yordamı, belirttiğiniz bir *parametre listesi* yordam adı hemen ardından parantez içinde.</span><span class="sxs-lookup"><span data-stu-id="73c23-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="73c23-113">Her parametre için bir ad, bir veri türü ve geçirme mekanizması belirtin ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="73c23-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="73c23-114">Ayrıca, bir parametrenin isteğe bağlı olduğunu gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="73c23-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="73c23-115">Bu, çağrıyı yapan kod için bir değer geçirmek yok anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="73c23-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="73c23-116">Her parametre adı görevi gören bir *yerel değişken* yordamda.</span><span class="sxs-lookup"><span data-stu-id="73c23-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="73c23-117">Parametre adı başka bir değişken aynı şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="73c23-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="73c23-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="73c23-118">Arguments</span></span>  
 <span data-ttu-id="73c23-119">Bir *bağımsız değişkeni* yordam çağrısı yükleyen bir yordam parametresini geçirdiğiniz değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73c23-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="73c23-120">Yordam çağrıları, çağrıyı yapan kod bağımsız değişkenler sağlar.</span><span class="sxs-lookup"><span data-stu-id="73c23-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="73c23-121">Çağırdığınızda bir `Function` veya `Sub` yordamı, eklediğiniz bir *bağımsız değişken listesi* yordam adı hemen ardından parantez içinde.</span><span class="sxs-lookup"><span data-stu-id="73c23-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="73c23-122">Her değişken parametre aynı konumda yer alan listesindeki karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="73c23-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="73c23-123">Parametre tanımına aksine, bağımsız değişken adları yok.</span><span class="sxs-lookup"><span data-stu-id="73c23-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="73c23-124">Her bir bağımsız değişkeni sıfır veya daha fazla değişkenlerinin, sabitleri ve değişmez değerleri içeren bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="73c23-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="73c23-125">Değerlendirilmiş ifadeyi veri türüne karşılık gelen bir parametre için tanımlanan veri türü genellikle eşleşmelidir ve her durumda parametre türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73c23-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c23-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73c23-126">See Also</span></span>  
 [<span data-ttu-id="73c23-127">Yordamları</span><span class="sxs-lookup"><span data-stu-id="73c23-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="73c23-128">Alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="73c23-128">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="73c23-129">İşlev yordamları</span><span class="sxs-lookup"><span data-stu-id="73c23-129">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="73c23-130">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="73c23-130">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="73c23-131">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="73c23-131">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="73c23-132">Nasıl yapılır: bir yordamın parametresini tanımlama</span><span class="sxs-lookup"><span data-stu-id="73c23-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="73c23-133">Nasıl yapılır: bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="73c23-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="73c23-134">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="73c23-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="73c23-135">Özyinelemeli yordamlar</span><span class="sxs-lookup"><span data-stu-id="73c23-135">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="73c23-136">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="73c23-136">Procedure Overloading</span></span>](./procedure-overloading.md)
