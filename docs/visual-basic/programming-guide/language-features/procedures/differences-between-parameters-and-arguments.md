---
description: 'Hakkında daha fazla bilgi edinin: parametreler ve bağımsız değişkenler arasındaki farklar (Visual Basic)'
title: Parametreler ve Bağımsız Değişkenler Arasındaki Farklar
ms.date: 07/20/2015
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
ms.openlocfilehash: 01efc7dc3f451d6aae20cfd091355f531af4431c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438768"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="373cc-103">Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="373cc-103">Differences Between Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="373cc-104">Çoğu durumda, bir yordamın çağrıldığı koşullara ilişkin bazı bilgileri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="373cc-104">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="373cc-105">Yinelenen veya paylaşılan görevler gerçekleştiren bir yordam, her çağrı için farklı bilgiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="373cc-105">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="373cc-106">Bu bilgiler, çağırdığınızda yordama geçirdiğiniz değişkenlerin, sabitlerin ve ifadelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="373cc-106">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="373cc-107">Bu bilgileri yordamla iletmek için, yordam bir *parametreyi* tanımlar ve çağıran kod bu parametreye bir *bağımsız değişken* geçirir.</span><span class="sxs-lookup"><span data-stu-id="373cc-107">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="373cc-108">Parametresini bir park alanı ve bağımsız değişkeni olarak bir otomobil olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="373cc-108">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="373cc-109">Farklı otomobil bir park alanını farklı zamanlarda park edebilir gibi, çağıran kod, yordamı her çağırdığında aynı parametreye farklı bir bağımsız değişken geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="373cc-109">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="373cc-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="373cc-110">Parameters</span></span>  

 <span data-ttu-id="373cc-111">Bir *parametre* , bu işlemi çağırdığınızda yordamın geçirilmesini beklediği bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="373cc-111">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="373cc-112">Yordamın bildirimi, parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="373cc-112">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="373cc-113">Bir `Function` veya `Sub` yordamı tanımladığınızda, yordam adından hemen sonra parantez içinde bir *parametre listesi* belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="373cc-113">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="373cc-114">Her parametre için bir ad, veri türü ve bir geçirme mekanizması ([ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md)) belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="373cc-114">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="373cc-115">Ayrıca, bir parametresinin isteğe bağlı olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="373cc-115">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="373cc-116">Bu, çağıran kodun bunun için bir değer geçmesi gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="373cc-116">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="373cc-117">Her parametrenin adı, yordamda *yerel bir değişken* işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="373cc-117">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="373cc-118">Parametre adını başka herhangi bir değişken kullandığınız şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="373cc-118">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="373cc-119">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="373cc-119">Arguments</span></span>  

 <span data-ttu-id="373cc-120">Bir *bağımsız değişken* , yordamı çağırdığınızda bir yordam parametresine geçirdiğiniz değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="373cc-120">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="373cc-121">Çağıran kod, yordamı çağırdığında bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="373cc-121">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="373cc-122">Bir `Function` veya `Sub` yordamını çağırdığınızda, yordam adının hemen ardından parantez içine bir *bağımsız değişken listesi* dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="373cc-122">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="373cc-123">Her bağımsız değişken, listedeki aynı konumdaki parametreye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="373cc-123">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="373cc-124">Parametre tanımının aksine bağımsız değişkenlerin adları yoktur.</span><span class="sxs-lookup"><span data-stu-id="373cc-124">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="373cc-125">Her bağımsız değişken sıfır veya daha fazla değişken, sabit ve değişmez değer içerebilen bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="373cc-125">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="373cc-126">Değerlendirilen ifadenin veri türü genellikle karşılık gelen parametre için tanımlanan veri türüyle eşleşir ve herhangi bir durumda parametre türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="373cc-126">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="373cc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="373cc-127">See also</span></span>

- [<span data-ttu-id="373cc-128">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="373cc-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="373cc-129">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="373cc-129">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="373cc-130">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="373cc-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="373cc-131">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="373cc-131">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="373cc-132">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="373cc-132">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="373cc-133">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="373cc-133">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="373cc-134">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="373cc-134">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="373cc-135">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="373cc-135">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="373cc-136">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="373cc-136">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="373cc-137">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="373cc-137">Procedure Overloading</span></span>](./procedure-overloading.md)
