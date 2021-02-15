---
description: 'Daha fazla bilgi edinin: yordam parametreleri ve bağımsız değişkenler (Visual Basic)'
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
ms.openlocfilehash: c2239c76450f503e74dbf5f191cd212e05d11600
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423166"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="7dacc-103">Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dacc-103">Procedure Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="7dacc-104">Çoğu durumda, bir yordam çağrıldığı koşullara ilişkin bazı bilgilere ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="7dacc-104">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="7dacc-105">Yinelenen veya paylaşılan görevler gerçekleştiren bir yordam, her çağrı için farklı bilgiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="7dacc-105">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="7dacc-106">Bu bilgiler, çağırdığınızda yordama geçirdiğiniz değişkenlerin, sabitlerin ve ifadelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="7dacc-106">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="7dacc-107">Bir *parametre* , yordamı çağırdığınızda belirtmeniz beklenen bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7dacc-107">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="7dacc-108">Yordamın bildirimi, parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7dacc-108">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="7dacc-109">Parametresiz, bir parametre veya birden fazla parametre içermeyen bir yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dacc-109">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="7dacc-110">Yordam tanımının parametreleri belirten bölümü *parametre listesi* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7dacc-110">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="7dacc-111">Bir *bağımsız değişken* , yordamı çağırdığınızda bir yordam parametresine sağladığınız değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7dacc-111">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="7dacc-112">Çağıran kod, yordamı çağırdığında bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7dacc-112">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="7dacc-113">Yordam çağrısının bağımsız değişkenleri belirten kısmına *bağımsız değişken listesi* denir.</span><span class="sxs-lookup"><span data-stu-id="7dacc-113">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="7dacc-114">Aşağıdaki çizim, iki farklı yerden yordam çağıran kodu gösterir `safeSquareRoot` .</span><span class="sxs-lookup"><span data-stu-id="7dacc-114">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="7dacc-115">İlk çağrı, değişkenin değerini `x` (4,0) parametresine geçirir `number` ve `root` (2,0) içindeki dönüş değeri değişkenine atanır `y` .</span><span class="sxs-lookup"><span data-stu-id="7dacc-115">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="7dacc-116">İkinci çağrı 9,0 sabit değerini ' a geçirir `number` ve dönüş değerini (3,0) değişkenine atar `z` .</span><span class="sxs-lookup"><span data-stu-id="7dacc-116">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Bir parametreye bağımsız değişken geçirmeyi gösteren diyagram](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="7dacc-118">Daha fazla bilgi için bkz. [Parametreler ve bağımsız değişkenler arasındaki farklar](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="7dacc-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="7dacc-119">Parametre veri türü</span><span class="sxs-lookup"><span data-stu-id="7dacc-119">Parameter Data Type</span></span>  

 <span data-ttu-id="7dacc-120">Bildiriminde yan tümcesini kullanarak bir parametre için veri türü tanımlarsınız `As` .</span><span class="sxs-lookup"><span data-stu-id="7dacc-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="7dacc-121">Örneğin, aşağıdaki işlev bir dizeyi ve bir tamsayıyı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="7dacc-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="7dacc-122">Tür denetleme anahtarı ([Option Strict deyimi](../../../language-reference/statements/option-strict-statement.md)) `Off,` yan tümcesi ise, `As` herhangi bir parametre kullanıyorsa, tüm parametrelerin onu kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7dacc-122">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="7dacc-123">Tür denetlemesi ise, `On` `As` yan tümce tüm yordam parametreleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7dacc-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="7dacc-124">Çağıran kod, bir parametre gibi karşılık gelen parametresinden farklı bir veri türüne sahip bir bağımsız değişken sağlamayı bekliyorsa `Byte` `String` , aşağıdakilerden birini yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="7dacc-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="7dacc-125">Yalnızca parametre veri türüne genişletip veri türlerine sahip bağımsız değişkenler sağlayın;</span><span class="sxs-lookup"><span data-stu-id="7dacc-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="7dacc-126">`Option Strict Off`Örtülü daraltma dönüştürmelerine izin vermek için ayarlayın; veya</span><span class="sxs-lookup"><span data-stu-id="7dacc-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="7dacc-127">Veri türünü açık bir şekilde dönüştürmek için bir dönüştürme anahtar sözcüğü kullanın.</span><span class="sxs-lookup"><span data-stu-id="7dacc-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="7dacc-128">Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="7dacc-128">Type Parameters</span></span>  

 <span data-ttu-id="7dacc-129">*Genel yordam* , normal parametrelerine ek olarak bir veya daha fazla *tür parametresi* de tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7dacc-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="7dacc-130">Genel yordam, çağıran kodun yordamı her çağırdığında farklı veri türlerini geçmesine izin verir, böylece veri türlerini her bir çağrının gereksinimlerine uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dacc-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="7dacc-131">Bkz. [Visual Basic genel yordamlar](../data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7dacc-131">See [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dacc-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dacc-132">See also</span></span>

- [<span data-ttu-id="7dacc-133">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="7dacc-133">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7dacc-134">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="7dacc-134">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="7dacc-135">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="7dacc-135">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="7dacc-136">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="7dacc-136">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="7dacc-137">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="7dacc-137">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="7dacc-138">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="7dacc-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="7dacc-139">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="7dacc-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="7dacc-140">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="7dacc-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="7dacc-141">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="7dacc-141">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="7dacc-142">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="7dacc-142">Type Conversions in Visual Basic</span></span>](../data-types/type-conversions.md)
