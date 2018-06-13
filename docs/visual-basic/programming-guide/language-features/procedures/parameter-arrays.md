---
title: Parametre Dizileri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: a91da0d9e16ff11fdd4980588fee64b3e4a603c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652383"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="074e5-102">Parametre Dizileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="074e5-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="074e5-103">Genellikle, bir yordam yordamı bildirimi belirtilenden daha fazla bağımsız değişkenlerle çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="074e5-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="074e5-104">Sonsuz sayıda bağımsız değişken gerektiğinde bildirebilir bir *parametre dizisi*, bir parametre için değer bir dizi kabul etmek bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="074e5-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="074e5-105">Yordam tanımlarsanız parametre dizisindeki öğelerin sayısı bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="074e5-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="074e5-106">Dizi boyutu, tek tek her yordam çağrısına tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="074e5-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="074e5-107">Bir ParamArray bildirme</span><span class="sxs-lookup"><span data-stu-id="074e5-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="074e5-108">Kullandığınız [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametre listesinde bir parametre dizisi belirtmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="074e5-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="074e5-109">Aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="074e5-109">The following rules apply:</span></span>  
  
-   <span data-ttu-id="074e5-110">Bu yordamı tanımı'nda son parametre olmalıdır ve bir yordam yalnızca bir parametre dizisi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="074e5-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
-   <span data-ttu-id="074e5-111">Parametre dizisi değere göre geçirilecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="074e5-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="074e5-112">Açık içerecek şekilde uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordamı tanımı bir anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="074e5-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
-   <span data-ttu-id="074e5-113">Parametre dizisine otomatik olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="074e5-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="074e5-114">Parametre dizinin öğe türü boş bir tek boyutlu dizi kendi varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="074e5-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
-   <span data-ttu-id="074e5-115">Parametre dizisi önceki tüm parametreler gerekli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="074e5-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="074e5-116">Parametre dizisi yalnızca isteğe bağlı bir parametre olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="074e5-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="074e5-117">Bir ParamArray çağırma</span><span class="sxs-lookup"><span data-stu-id="074e5-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="074e5-118">Bir parametre dizisi tanımlayan bir yordam çağrısı, bağımsız değişkeni aşağıdaki yollardan birinde sağlayabilir:</span><span class="sxs-lookup"><span data-stu-id="074e5-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
-   <span data-ttu-id="074e5-119">Hiçbir şey — diğer bir deyişle, atlayabilirsiniz [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="074e5-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="074e5-120">Bu durumda, boş bir dizi yordama geçirilir.</span><span class="sxs-lookup"><span data-stu-id="074e5-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="074e5-121">Ayrıca iletebilirsiniz [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) aynı etkiye sahip anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="074e5-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
-   <span data-ttu-id="074e5-122">Bir rastgele sayıda bağımsız değişken, virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="074e5-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="074e5-123">Her bağımsız değişkeninin veri türü örtük olarak dönüştürülebilir olmalıdır `ParamArray` öğe türü.</span><span class="sxs-lookup"><span data-stu-id="074e5-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
-   <span data-ttu-id="074e5-124">Parametre dizinin öğe türü olarak aynı öğe türüne sahip bir dizi.</span><span class="sxs-lookup"><span data-stu-id="074e5-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="074e5-125">Her durumda, yordam içindeki kod aynı veri türünde öğelerin tek boyutlu bir dizi olarak parametre dizisi değerlendirir `ParamArray` veri türü.</span><span class="sxs-lookup"><span data-stu-id="074e5-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="074e5-126">Süresiz olarak büyük olabilen bir dizi ile ilgilenir olduğunda, uygulamanızın iç bazı kapasite taşmasını riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="074e5-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="074e5-127">Bir parametre dizisi kabul ederseniz, çağrıyı yapan kod kendisine geçirilen dizi boyutu için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="074e5-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="074e5-128">Uygulamanız için çok büyük ise uygun adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="074e5-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="074e5-129">Daha fazla bilgi için bkz: [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="074e5-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="074e5-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="074e5-130">Example</span></span>  
 <span data-ttu-id="074e5-131">Aşağıdaki örnek tanımlar ve işlev çağrılarını `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="074e5-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="074e5-132">`ParamArray` Parametresi değiştiricisi `args` değişken sayıda bağımsız değişken kabul etmek işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="074e5-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 <span data-ttu-id="074e5-133">Aşağıdaki örnekte bir parametre dizisi yordamla tanımlar ve parametre dizisine geçirilen tüm dizi öğelerinin değerlerini çıkarır.</span><span class="sxs-lookup"><span data-stu-id="074e5-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="074e5-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="074e5-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="074e5-135">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="074e5-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="074e5-136">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="074e5-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="074e5-137">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="074e5-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="074e5-138">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="074e5-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="074e5-139">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="074e5-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="074e5-140">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="074e5-140">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="074e5-141">Diziler</span><span class="sxs-lookup"><span data-stu-id="074e5-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="074e5-142">Optional</span><span class="sxs-lookup"><span data-stu-id="074e5-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
