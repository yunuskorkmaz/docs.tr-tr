---
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
ms.openlocfilehash: dd0a62b6567f3e74763b7f2e9b96803c193c7976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403362"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="0ce18-102">Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce18-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="0ce18-103">Çoğu durumda, bir yordamın çağrıldığı koşullara ilişkin bazı bilgileri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ce18-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="0ce18-104">Yinelenen veya paylaşılan görevler gerçekleştiren bir yordam, her çağrı için farklı bilgiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ce18-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="0ce18-105">Bu bilgiler, çağırdığınızda yordama geçirdiğiniz değişkenlerin, sabitlerin ve ifadelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="0ce18-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="0ce18-106">Bu bilgileri yordamla iletmek için, yordam bir *parametreyi*tanımlar ve çağıran kod bu parametreye bir *bağımsız değişken* geçirir.</span><span class="sxs-lookup"><span data-stu-id="0ce18-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="0ce18-107">Parametresini bir park alanı ve bağımsız değişkeni olarak bir otomobil olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce18-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="0ce18-108">Farklı otomobil bir park alanını farklı zamanlarda park edebilir gibi, çağıran kod, yordamı her çağırdığında aynı parametreye farklı bir bağımsız değişken geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="0ce18-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="0ce18-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ce18-109">Parameters</span></span>  
 <span data-ttu-id="0ce18-110">Bir *parametre* , bu işlemi çağırdığınızda yordamın geçirilmesini beklediği bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ce18-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="0ce18-111">Yordamın bildirimi, parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ce18-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="0ce18-112">Bir `Function` veya `Sub` yordamı tanımladığınızda, yordam adından hemen sonra parantez içinde bir *parametre listesi* belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce18-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="0ce18-113">Her parametre için bir ad, veri türü ve bir geçirme mekanizması ([ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md)) belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce18-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="0ce18-114">Ayrıca, bir parametresinin isteğe bağlı olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce18-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="0ce18-115">Bu, çağıran kodun bunun için bir değer geçmesi gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0ce18-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="0ce18-116">Her parametrenin adı, yordamda *yerel bir değişken* işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="0ce18-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="0ce18-117">Parametre adını başka herhangi bir değişken kullandığınız şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0ce18-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="0ce18-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="0ce18-118">Arguments</span></span>  
 <span data-ttu-id="0ce18-119">Bir *bağımsız değişken* , yordamı çağırdığınızda bir yordam parametresine geçirdiğiniz değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ce18-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="0ce18-120">Çağıran kod, yordamı çağırdığında bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ce18-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="0ce18-121">Bir `Function` veya `Sub` yordamını çağırdığınızda, yordam adının hemen ardından parantez içine bir *bağımsız değişken listesi* dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce18-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="0ce18-122">Her bağımsız değişken, listedeki aynı konumdaki parametreye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0ce18-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="0ce18-123">Parametre tanımının aksine bağımsız değişkenlerin adları yoktur.</span><span class="sxs-lookup"><span data-stu-id="0ce18-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="0ce18-124">Her bağımsız değişken sıfır veya daha fazla değişken, sabit ve değişmez değer içerebilen bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="0ce18-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="0ce18-125">Değerlendirilen ifadenin veri türü genellikle karşılık gelen parametre için tanımlanan veri türüyle eşleşir ve herhangi bir durumda parametre türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ce18-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce18-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ce18-126">See also</span></span>

- [<span data-ttu-id="0ce18-127">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0ce18-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0ce18-128">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0ce18-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="0ce18-129">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="0ce18-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="0ce18-130">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="0ce18-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0ce18-131">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="0ce18-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0ce18-132">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0ce18-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="0ce18-133">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="0ce18-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="0ce18-134">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="0ce18-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="0ce18-135">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0ce18-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="0ce18-136">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="0ce18-136">Procedure Overloading</span></span>](./procedure-overloading.md)
