---
title: Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 42f85ed98f399c96f89879129b085f25ab117096
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731744"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="4dcef-102">Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dcef-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="4dcef-103">Çoğu durumda, bir yordam içinde bunu çağrıldıktan koşullar hakkında bazı bilgiler gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="4dcef-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="4dcef-104">Yinelenen veya paylaşılan görevleri gerçekleştiren bir yordam her çağrı için farklı bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4dcef-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="4dcef-105">Bu bilgiler, değişkenleri, sabitleri ve onu çağırdığınızda yordama geçirdiğiniz ifadeleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="4dcef-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="4dcef-106">A *parametre* yordamı çağırdığınızda, temin etmeniz bekliyor. bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4dcef-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="4dcef-107">Yordam bildirimi parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4dcef-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="4dcef-108">Bir yordam parametre, bir parametre veya birden fazla tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4dcef-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="4dcef-109">Parametreleri belirtir bir yordam tanımının bir parçası olarak adlandırılan *parametre listesi*.</span><span class="sxs-lookup"><span data-stu-id="4dcef-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="4dcef-110">Bir *bağımsız değişken* yordamı çağırdığınızda, sağladığınız değerin bir yordamın parametresini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4dcef-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="4dcef-111">Yordamı çağırdığında, çağıran kodun bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4dcef-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="4dcef-112">Bağımsız değişkenleri belirten yordam çağrısı bir parçası olarak adlandırılan *bağımsız değişken listesi*.</span><span class="sxs-lookup"><span data-stu-id="4dcef-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="4dcef-113">Yordamı çağırma kodu aşağıdaki çizimde `safeSquareRoot` iki farklı yerde.</span><span class="sxs-lookup"><span data-stu-id="4dcef-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="4dcef-114">İlk çağrı değişkenin değeri olarak geçirir `x` (4.0) parametresine `number`ve dönüş değeri `root` (2.0) değişkenine atanan `y`.</span><span class="sxs-lookup"><span data-stu-id="4dcef-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="4dcef-115">Değişmez değer 9.0 için yapılan ikinci çağrı geçirir `number`ve dönüş değeri (3.0) değişkene atar `z`.</span><span class="sxs-lookup"><span data-stu-id="4dcef-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 <span data-ttu-id="4dcef-116">![Parametresi için bağımsız değişken geçirme grafik diyagramı](./media/parametersargue.gif "ParametersArgue")</span><span class="sxs-lookup"><span data-stu-id="4dcef-116">![Graphic diagram of passing argument to parameter](./media/parametersargue.gif "ParametersArgue")</span></span>  
<span data-ttu-id="4dcef-117">Bir parametre bağımsız değişken geçirme</span><span class="sxs-lookup"><span data-stu-id="4dcef-117">Passing an argument to a parameter</span></span>  
  
 <span data-ttu-id="4dcef-118">Daha fazla bilgi için [arasındaki farklar parametreler ve bağımsız değişkenler](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4dcef-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="4dcef-119">Parametre veri türü</span><span class="sxs-lookup"><span data-stu-id="4dcef-119">Parameter Data Type</span></span>  
 <span data-ttu-id="4dcef-120">Bir parametrenin veri türünü kullanarak tanımladığınız `As` bildiriminden yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4dcef-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="4dcef-121">Örneğin, aşağıdaki işlev bir dize ve tamsayı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4dcef-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 <span data-ttu-id="4dcef-122">Tür denetleme geçerseniz ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `Off,` `As` yan tümcesi, isteğe bağlıdır, hariç, herhangi bir parametre kullanıyorsa, tüm parametreleri onu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4dcef-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="4dcef-123">Tür denetleme ise `On`, `As` yan tümcesi tüm parametreler için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4dcef-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="4dcef-124">Çağıran kod gibi bir bağımsız değişkeni, karşılık gelen parametresinin farklı bir veri türü ile sağlamak bekliyor durumunda `Byte` için bir `String` parametresi, aşağıdakilerden birini yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="4dcef-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="4dcef-125">Kaynağı yalnızca bağımsız değişkenler için parametre veri türü genişletmek veri türleriyle;</span><span class="sxs-lookup"><span data-stu-id="4dcef-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="4dcef-126">Ayarlama `Option Strict Off` daraltma dönüştürmelerini örtülü; izin vermek veya</span><span class="sxs-lookup"><span data-stu-id="4dcef-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="4dcef-127">Dönüştürme anahtar sözcüğü, veri türüne açıkça dönüştürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4dcef-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="4dcef-128">Tür ParameTReleri</span><span class="sxs-lookup"><span data-stu-id="4dcef-128">Type Parameters</span></span>  
 <span data-ttu-id="4dcef-129">A *genel yordam* ayrıca bir veya daha fazla tanımlar *tür parametrelerindeki* normal parametrelerini yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="4dcef-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="4dcef-130">Çağıran kod, veri türleri için her bir çağrıyı gereksinimlerini karşılayacak hale getirebilirsiniz şekilde yordamı, çağırdığı her zaman geçiş farklı veri türleri genel bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="4dcef-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="4dcef-131">Bkz: [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4dcef-131">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dcef-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dcef-132">See also</span></span>
- [<span data-ttu-id="4dcef-133">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4dcef-133">Procedures</span></span>](./index.md)
- [<span data-ttu-id="4dcef-134">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4dcef-134">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="4dcef-135">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="4dcef-135">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="4dcef-136">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="4dcef-136">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="4dcef-137">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="4dcef-137">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="4dcef-138">Nasıl yapılır: Bir yordamın parametresini tanımlama</span><span class="sxs-lookup"><span data-stu-id="4dcef-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="4dcef-139">Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="4dcef-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="4dcef-140">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="4dcef-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="4dcef-141">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="4dcef-141">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="4dcef-142">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="4dcef-142">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
