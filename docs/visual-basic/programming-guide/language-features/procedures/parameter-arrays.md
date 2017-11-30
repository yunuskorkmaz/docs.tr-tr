---
title: Parametre Dizileri (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ca2b5f02ac4fb3eb613488c8a9852eb2aa4ce5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="770e8-102">Parametre Dizileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="770e8-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="770e8-103">Genellikle, bir yordam yordamı bildirimi belirtilenden daha fazla bağımsız değişkenlerle çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="770e8-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="770e8-104">Sonsuz sayıda bağımsız değişken gerektiğinde bildirebilir bir *parametre dizisi*, bir parametre için değer bir dizi kabul etmek bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="770e8-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="770e8-105">Yordam tanımlarsanız parametre dizisindeki öğelerin sayısı bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="770e8-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="770e8-106">Dizi boyutu, tek tek her yordam çağrısına tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="770e8-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="770e8-107">Bir ParamArray bildirme</span><span class="sxs-lookup"><span data-stu-id="770e8-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="770e8-108">Kullandığınız [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametre listesinde bir parametre dizisi belirtmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="770e8-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="770e8-109">Aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="770e8-109">The following rules apply:</span></span>  
  
-   <span data-ttu-id="770e8-110">Bu yordamı tanımı'nda son parametre olmalıdır ve bir yordam yalnızca bir parametre dizisi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="770e8-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
-   <span data-ttu-id="770e8-111">Parametre dizisi değere göre geçirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="770e8-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="770e8-112">Açık içerecek şekilde uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordamı tanımı bir anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="770e8-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
-   <span data-ttu-id="770e8-113">Parametre dizisine otomatik olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="770e8-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="770e8-114">Parametre dizinin öğe türü boş bir tek boyutlu dizi kendi varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="770e8-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
-   <span data-ttu-id="770e8-115">Parametre dizisi önceki tüm parametreler gerekli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="770e8-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="770e8-116">Parametre dizisi yalnızca isteğe bağlı bir parametre olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="770e8-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="770e8-117">Bir ParamArray çağırma</span><span class="sxs-lookup"><span data-stu-id="770e8-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="770e8-118">Bir parametre dizisi tanımlayan bir yordam çağrısı, bağımsız değişkeni aşağıdaki yollardan birinde sağlayabilir:</span><span class="sxs-lookup"><span data-stu-id="770e8-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
-   <span data-ttu-id="770e8-119">Hiçbir şey — diğer bir deyişle, atlayabilirsiniz [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="770e8-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="770e8-120">Bu durumda, boş bir dizi yordama geçirilir.</span><span class="sxs-lookup"><span data-stu-id="770e8-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="770e8-121">Ayrıca iletebilirsiniz [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) aynı etkiye sahip anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="770e8-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
-   <span data-ttu-id="770e8-122">Bir rastgele sayıda bağımsız değişken, virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="770e8-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="770e8-123">Her bağımsız değişkeninin veri türü örtük olarak dönüştürülebilir olmalıdır `ParamArray` öğe türü.</span><span class="sxs-lookup"><span data-stu-id="770e8-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
-   <span data-ttu-id="770e8-124">Parametre dizinin öğe türü olarak aynı öğe türüne sahip bir dizi.</span><span class="sxs-lookup"><span data-stu-id="770e8-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="770e8-125">Her durumda, yordam içindeki kod aynı veri türünde öğelerin tek boyutlu bir dizi olarak parametre dizisi değerlendirir `ParamArray` veri türü.</span><span class="sxs-lookup"><span data-stu-id="770e8-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="770e8-126">Süresiz olarak büyük olabilen bir dizi ile ilgilenir olduğunda, uygulamanızın iç bazı kapasite taşmasını riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="770e8-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="770e8-127">Bir parametre dizisi kabul ederseniz, çağrıyı yapan kod kendisine geçirilen dizi boyutu için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="770e8-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="770e8-128">Uygulamanız için çok büyük ise uygun adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="770e8-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="770e8-129">Daha fazla bilgi için bkz: [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="770e8-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="770e8-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="770e8-130">Example</span></span>  
 <span data-ttu-id="770e8-131">Aşağıdaki örnek tanımlar ve işlev çağrılarını `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="770e8-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="770e8-132">`ParamArray` Parametresi değiştiricisi `args` değişken sayıda bağımsız değişken kabul etmek işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="770e8-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 <span data-ttu-id="770e8-133">Aşağıdaki örnekte bir parametre dizisi yordamla tanımlar ve parametre dizisine geçirilen tüm dizi öğelerinin değerlerini çıkarır.</span><span class="sxs-lookup"><span data-stu-id="770e8-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="770e8-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="770e8-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="770e8-135">Yordamları</span><span class="sxs-lookup"><span data-stu-id="770e8-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="770e8-136">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="770e8-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="770e8-137">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="770e8-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="770e8-138">Bağımsız değişkenleri konuma göre ve ada göre geçirme</span><span class="sxs-lookup"><span data-stu-id="770e8-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="770e8-139">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="770e8-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="770e8-140">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="770e8-140">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="770e8-141">Diziler</span><span class="sxs-lookup"><span data-stu-id="770e8-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="770e8-142">İsteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="770e8-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
