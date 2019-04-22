---
title: Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
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
ms.openlocfilehash: a69b956c7cffcc2a26916d6fc92f23dd4e2322d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838982"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="f2865-102">Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2865-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="f2865-103">Çoğu durumda, bir yordam içinde bunu çağrıldıktan koşullar hakkında bazı bilgiler olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2865-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="f2865-104">Yinelenen veya paylaşılan görevleri gerçekleştiren bir yordam her çağrı için farklı bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2865-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="f2865-105">Bu bilgiler, değişkenleri, sabitleri ve onu çağırdığınızda yordama geçirdiğiniz ifadeleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="f2865-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="f2865-106">Bu yordamı bilgiler iletmek için yordamı tanımlar. bir *parametre*, ve çağıran kod geçirir bir *bağımsız değişken* parametreye.</span><span class="sxs-lookup"><span data-stu-id="f2865-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="f2865-107">Parametre olarak park boşluk ve bağımsız değişken bir otomobilin olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2865-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="f2865-108">Yalnızca farklı otomobil park boşluk farklı zamanlarda park gibi çağıran kodun BT'nin yordam çağrıları her zaman aynı parametresi için farklı bir bağımsız değişken geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2865-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="f2865-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2865-109">Parameters</span></span>  
 <span data-ttu-id="f2865-110">A *parametre* yordamı çağırdığınızda, geçirmeniz bekliyor. bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2865-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="f2865-111">Yordam bildirimi parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2865-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="f2865-112">Tanımladığınızda bir `Function` veya `Sub` yordamı, belirttiğiniz bir *parametre listesi* yordam adına hemen arkasından parantez içinde.</span><span class="sxs-lookup"><span data-stu-id="f2865-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="f2865-113">Her parametre için bir ad, bir veri türü ve geçirme mekanizma belirtin ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="f2865-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="f2865-114">Ayrıca, bir parametrenin isteğe bağlı olduğunu gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f2865-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="f2865-115">Başka bir deyişle, çağırma kodunun kendisi için bir değer geçirmek yok.</span><span class="sxs-lookup"><span data-stu-id="f2865-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="f2865-116">Her parametre adı olarak hizmet veren bir *yerel değişken* yordamda.</span><span class="sxs-lookup"><span data-stu-id="f2865-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="f2865-117">Parametre adı herhangi bir değişken aynı şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f2865-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="f2865-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="f2865-118">Arguments</span></span>  
 <span data-ttu-id="f2865-119">Bir *bağımsız değişken* yordamı çağırdığınızda bir yordam parametresi için geçirdiğiniz değer temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2865-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="f2865-120">Yordamı çağırdığında, çağıran kodun bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2865-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="f2865-121">Çağırdığınızda bir `Function` veya `Sub` yordamı, eklediğiniz bir *bağımsız değişken listesi* yordam adına hemen arkasından parantez içinde.</span><span class="sxs-lookup"><span data-stu-id="f2865-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="f2865-122">Her bağımsız değişken listesinde aynı konumda parametresine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f2865-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="f2865-123">Parametre tanımında aksine, bağımsız değişken adları yok.</span><span class="sxs-lookup"><span data-stu-id="f2865-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="f2865-124">Her bağımsız değişkeni sıfır veya daha fazla değişkenler, sabitler ve sabit değerleri içeren bir ifade ' dir.</span><span class="sxs-lookup"><span data-stu-id="f2865-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="f2865-125">Değerlendirilmiş ifadeyi veri türüne karşılık gelen parametre için tanımlanan veri türü genellikle eşleşmesi gerekir ve her durumda parametre türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2865-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2865-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2865-126">See also</span></span>

- [<span data-ttu-id="f2865-127">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f2865-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f2865-128">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f2865-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="f2865-129">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="f2865-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="f2865-130">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="f2865-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="f2865-131">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="f2865-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f2865-132">Nasıl yapılır: Bir yordamın parametresini tanımlama</span><span class="sxs-lookup"><span data-stu-id="f2865-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="f2865-133">Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="f2865-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="f2865-134">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="f2865-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="f2865-135">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f2865-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="f2865-136">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f2865-136">Procedure Overloading</span></span>](./procedure-overloading.md)
