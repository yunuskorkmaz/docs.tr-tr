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
ms.openlocfilehash: 372d5fdd2702d6f85f784ee5addea91abe46d3bd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639011"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="264e3-102">Parametre Dizileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="264e3-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="264e3-103">Genellikle, yordam bildirimi belirtilenden daha fazla bağımsız değişken içeren bir yordamı çağıramaz.</span><span class="sxs-lookup"><span data-stu-id="264e3-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="264e3-104">Sonsuz sayıda bağımsız değişken gerektiğinde bildirebilirsiniz bir *parametre dizisi*, bir dizi parametre değerlerini kabul etmek bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="264e3-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="264e3-105">Yordamı tanımlarken parametresi dizideki öğelerin sayısını öğrenmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="264e3-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="264e3-106">Dizi boyutu, tek tek her yordam çağrısına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="264e3-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="264e3-107">Bir ParamArray bildirme</span><span class="sxs-lookup"><span data-stu-id="264e3-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="264e3-108">Kullandığınız [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametre listesinde bir parametre dizisi belirtmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="264e3-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="264e3-109">Aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="264e3-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="264e3-110">Bir yordam yalnızca bir parametre dizisi tanımlayabilirsiniz ve yordam tanımında son parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="264e3-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="264e3-111">Parametre dizisi değerine göre geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="264e3-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="264e3-112">İyi bir programlama açıkça içerecek şekilde [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordam tanımında anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="264e3-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="264e3-113">Parametre dizisi otomatik olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="264e3-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="264e3-114">Boş bir tek boyutlu dizi parametresi dizinin öğe türü, varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="264e3-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="264e3-115">Parametre dizisi önceki tüm parametreler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="264e3-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="264e3-116">Parametre dizisi, yalnızca isteğe bağlı parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="264e3-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="264e3-117">Bir ParamArray çağırma</span><span class="sxs-lookup"><span data-stu-id="264e3-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="264e3-118">Bir parametre dizisi tanımlayan bir yordamı çağırdığınızda, bağımsız değişkeni aşağıdaki yollardan birinde belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="264e3-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="264e3-119">Hiçbir şey — diğer bir deyişle, atlayabilirsiniz [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="264e3-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="264e3-120">Bu durumda, boş bir dizi yordamına geçirildi.</span><span class="sxs-lookup"><span data-stu-id="264e3-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="264e3-121">De geçirebilirsiniz [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) aynı etkiye sahip anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="264e3-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
- <span data-ttu-id="264e3-122">Rastgele bir sayıdan bağımsız değişkenleri, virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="264e3-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="264e3-123">Her bağımsız değişken veri türünü örtük olarak dönüştürülebilir olmalıdır `ParamArray` öğe türü.</span><span class="sxs-lookup"><span data-stu-id="264e3-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="264e3-124">Parametre dizinin öğe türü olarak aynı öğe türüne sahip bir dizi.</span><span class="sxs-lookup"><span data-stu-id="264e3-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="264e3-125">Her durumda, yordamı içindeki kod öğelerini aynı veri türünde tek boyutlu bir dizi olarak parametre dizisi işler `ParamArray` veri türü.</span><span class="sxs-lookup"><span data-stu-id="264e3-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="264e3-126">Süresiz olarak büyük olabilecek bir dizi işlem olduğunda, uygulamanızın bazı iç kapasite taşmasını riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="264e3-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="264e3-127">Bir parametre dizisi kabul ederseniz, çağıran kodun geçirilen dizinin boyutu için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="264e3-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="264e3-128">Uygulamanız için çok büyük ise, uygun adımları atıyoruz.</span><span class="sxs-lookup"><span data-stu-id="264e3-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="264e3-129">Daha fazla bilgi için [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="264e3-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="264e3-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="264e3-130">Example</span></span>  
 <span data-ttu-id="264e3-131">Aşağıdaki örnek, tanımlar ve işlev çağrıları `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="264e3-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="264e3-132">`ParamArray` Parametresi değiştiricisi `args` değişken sayıda bağımsız değişken kabul etmek bu işlevi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="264e3-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="264e3-133">Aşağıdaki örnek, bir parametre dizisi içeren bir yordamı tanımlar ve geçirilen parametre dizisi için tüm dizi öğelerinin değerleri çıkarır.</span><span class="sxs-lookup"><span data-stu-id="264e3-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="264e3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="264e3-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="264e3-135">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="264e3-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="264e3-136">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="264e3-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="264e3-137">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="264e3-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="264e3-138">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="264e3-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="264e3-139">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="264e3-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="264e3-140">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="264e3-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="264e3-141">Diziler</span><span class="sxs-lookup"><span data-stu-id="264e3-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="264e3-142">Optional</span><span class="sxs-lookup"><span data-stu-id="264e3-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
