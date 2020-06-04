---
title: Yordam Parametreleri ve Bağımsız Değişkenleri
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
ms.openlocfilehash: 178206ca2ee103bbdb5a4ac03bca0df903c8c5d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406722"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="93782-102">Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93782-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="93782-103">Çoğu durumda, bir yordam çağrıldığı koşullara ilişkin bazı bilgilere ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="93782-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="93782-104">Yinelenen veya paylaşılan görevler gerçekleştiren bir yordam, her çağrı için farklı bilgiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="93782-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="93782-105">Bu bilgiler, çağırdığınızda yordama geçirdiğiniz değişkenlerin, sabitlerin ve ifadelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="93782-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="93782-106">Bir *parametre* , yordamı çağırdığınızda belirtmeniz beklenen bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="93782-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="93782-107">Yordamın bildirimi, parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="93782-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="93782-108">Parametresiz, bir parametre veya birden fazla parametre içermeyen bir yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93782-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="93782-109">Yordam tanımının parametreleri belirten bölümü *parametre listesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="93782-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="93782-110">Bir *bağımsız değişken* , yordamı çağırdığınızda bir yordam parametresine sağladığınız değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="93782-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="93782-111">Çağıran kod, yordamı çağırdığında bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="93782-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="93782-112">Yordam çağrısının bağımsız değişkenleri belirten kısmına *bağımsız değişken listesi*denir.</span><span class="sxs-lookup"><span data-stu-id="93782-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="93782-113">Aşağıdaki çizim, iki farklı yerden yordam çağıran kodu gösterir `safeSquareRoot` .</span><span class="sxs-lookup"><span data-stu-id="93782-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="93782-114">İlk çağrı, değişkenin değerini `x` (4,0) parametresine geçirir `number` ve `root` (2,0) içindeki dönüş değeri değişkenine atanır `y` .</span><span class="sxs-lookup"><span data-stu-id="93782-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="93782-115">İkinci çağrı 9,0 sabit değerini ' a geçirir `number` ve dönüş değerini (3,0) değişkenine atar `z` .</span><span class="sxs-lookup"><span data-stu-id="93782-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Bir parametreye bağımsız değişken geçirmeyi gösteren diyagram](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="93782-117">Daha fazla bilgi için bkz. [Parametreler ve bağımsız değişkenler arasındaki farklar](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="93782-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="93782-118">Parametre veri türü</span><span class="sxs-lookup"><span data-stu-id="93782-118">Parameter Data Type</span></span>  
 <span data-ttu-id="93782-119">Bildiriminde yan tümcesini kullanarak bir parametre için veri türü tanımlarsınız `As` .</span><span class="sxs-lookup"><span data-stu-id="93782-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="93782-120">Örneğin, aşağıdaki işlev bir dizeyi ve bir tamsayıyı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="93782-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="93782-121">Tür denetleme anahtarı ([Option Strict deyimi](../../../language-reference/statements/option-strict-statement.md)) `Off,` yan tümcesi ise, `As` herhangi bir parametre kullanıyorsa, tüm parametrelerin onu kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="93782-121">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="93782-122">Tür denetlemesi ise, `On` `As` yan tümce tüm yordam parametreleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="93782-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="93782-123">Çağıran kod, bir parametre gibi karşılık gelen parametresinden farklı bir veri türüne sahip bir bağımsız değişken sağlamayı bekliyorsa `Byte` `String` , aşağıdakilerden birini yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="93782-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="93782-124">Yalnızca parametre veri türüne genişletip veri türlerine sahip bağımsız değişkenler sağlayın;</span><span class="sxs-lookup"><span data-stu-id="93782-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="93782-125">`Option Strict Off`Örtülü daraltma dönüştürmelerine izin vermek için ayarlayın; veya</span><span class="sxs-lookup"><span data-stu-id="93782-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="93782-126">Veri türünü açık bir şekilde dönüştürmek için bir dönüştürme anahtar sözcüğü kullanın.</span><span class="sxs-lookup"><span data-stu-id="93782-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="93782-127">Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="93782-127">Type Parameters</span></span>  
 <span data-ttu-id="93782-128">*Genel yordam* , normal parametrelerine ek olarak bir veya daha fazla *tür parametresi* de tanımlar.</span><span class="sxs-lookup"><span data-stu-id="93782-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="93782-129">Genel yordam, çağıran kodun yordamı her çağırdığında farklı veri türlerini geçmesine izin verir, böylece veri türlerini her bir çağrının gereksinimlerine uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93782-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="93782-130">Bkz. [Visual Basic genel yordamlar](../data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="93782-130">See [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93782-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93782-131">See also</span></span>

- [<span data-ttu-id="93782-132">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="93782-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="93782-133">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="93782-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="93782-134">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="93782-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="93782-135">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="93782-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="93782-136">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="93782-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="93782-137">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="93782-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="93782-138">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="93782-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="93782-139">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="93782-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="93782-140">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="93782-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="93782-141">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="93782-141">Type Conversions in Visual Basic</span></span>](../data-types/type-conversions.md)
