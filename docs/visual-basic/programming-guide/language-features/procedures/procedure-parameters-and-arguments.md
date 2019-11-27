---
title: Parametreler ve Bağımsız Değişkenler
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
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352577"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="b4ba5-102">Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4ba5-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="b4ba5-103">Çoğu durumda, bir yordam çağrıldığı koşullara ilişkin bazı bilgilere ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="b4ba5-104">Yinelenen veya paylaşılan görevler gerçekleştiren bir yordam, her çağrı için farklı bilgiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="b4ba5-105">Bu bilgiler, çağırdığınızda yordama geçirdiğiniz değişkenlerin, sabitlerin ve ifadelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="b4ba5-106">Bir *parametre* , yordamı çağırdığınızda belirtmeniz beklenen bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="b4ba5-107">Yordamın bildirimi, parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="b4ba5-108">Parametresiz, bir parametre veya birden fazla parametre içermeyen bir yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="b4ba5-109">Yordam tanımının parametreleri belirten bölümü *parametre listesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="b4ba5-110">Bir *bağımsız değişken* , yordamı çağırdığınızda bir yordam parametresine sağladığınız değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="b4ba5-111">Çağıran kod, yordamı çağırdığında bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="b4ba5-112">Yordam çağrısının bağımsız değişkenleri belirten kısmına *bağımsız değişken listesi*denir.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="b4ba5-113">Aşağıdaki çizim, iki farklı yerden yordam `safeSquareRoot` çağıran kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="b4ba5-114">İlk çağrı `x` (4,0) değişkeninin değerini `number`parametresine geçirir ve `root` (2,0) içindeki dönüş değeri `y`değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="b4ba5-115">İkinci çağrı 9,0 sabit değerini `number`geçirir ve dönüş değerini (3,0) `z`değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Bir parametreye bağımsız değişken geçirmeyi gösteren diyagram](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="b4ba5-117">Daha fazla bilgi için bkz. [Parametreler ve bağımsız değişkenler arasındaki farklar](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="b4ba5-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="b4ba5-118">Parametre veri türü</span><span class="sxs-lookup"><span data-stu-id="b4ba5-118">Parameter Data Type</span></span>  
 <span data-ttu-id="b4ba5-119">Bir parametre için, bildiriminde `As` yan tümcesini kullanarak bir veri türü tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="b4ba5-120">Örneğin, aşağıdaki işlev bir dizeyi ve bir tamsayıyı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="b4ba5-121">Tür denetleme anahtarı ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) `Off,` `As` yan tümcesi isteğe bağlıdır, ancak herhangi bir parametre kullanıyorsa, tüm parametrelerin onu kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="b4ba5-122">Tür denetlemesi `On`, tüm yordam parametreleri için `As` yan tümcesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="b4ba5-123">Çağıran kod, `String` parametreye `Byte` gibi, karşılık gelen parametresinden farklı bir veri türüne sahip bir bağımsız değişken sağlamayı bekliyorsa, aşağıdakilerden birini yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b4ba5-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="b4ba5-124">Yalnızca parametre veri türüne genişletip veri türlerine sahip bağımsız değişkenler sağlayın;</span><span class="sxs-lookup"><span data-stu-id="b4ba5-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="b4ba5-125">Örtülü daraltma dönüştürmelerine izin vermek için `Option Strict Off` ayarlayın; veya</span><span class="sxs-lookup"><span data-stu-id="b4ba5-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="b4ba5-126">Veri türünü açık bir şekilde dönüştürmek için bir dönüştürme anahtar sözcüğü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="b4ba5-127">Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="b4ba5-127">Type Parameters</span></span>  
 <span data-ttu-id="b4ba5-128">*Genel yordam* , normal parametrelerine ek olarak bir veya daha fazla *tür parametresi* de tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="b4ba5-129">Genel yordam, çağıran kodun yordamı her çağırdığında farklı veri türlerini geçmesine izin verir, böylece veri türlerini her bir çağrının gereksinimlerine uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="b4ba5-130">Bkz. [Visual Basic genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b4ba5-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ba5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4ba5-131">See also</span></span>

- [<span data-ttu-id="b4ba5-132">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b4ba5-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b4ba5-133">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b4ba5-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="b4ba5-134">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="b4ba5-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="b4ba5-135">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="b4ba5-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b4ba5-136">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="b4ba5-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="b4ba5-137">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="b4ba5-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="b4ba5-138">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="b4ba5-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="b4ba5-139">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="b4ba5-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="b4ba5-140">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="b4ba5-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="b4ba5-141">Visual Basic dönüşümler yazın</span><span class="sxs-lookup"><span data-stu-id="b4ba5-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
