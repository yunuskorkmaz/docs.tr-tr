---
title: Parametre Dizileri
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
ms.openlocfilehash: 2c8c60015d834ffa3f8618dd98616350e13f0e5c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100665"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="9e315-102">Parametre Dizileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e315-102">Parameter Arrays (Visual Basic)</span></span>

<span data-ttu-id="9e315-103">Genellikle, yordam bildiriminin belirttiğinden daha fazla bağımsız değişkenle bir yordam çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e315-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="9e315-104">Sınırsız sayıda bağımsız değişkene ihtiyacınız olduğunda bir *parametre dizisi*bildirebilirsiniz ve bu, bir yordamın bir parametre için bir dizi değer kabul etmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9e315-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="9e315-105">Yordamı tanımlarken parametre dizisindeki öğelerin sayısını bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9e315-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="9e315-106">Dizi boyutu, yordamın her çağrısıyla ayrı ayrı belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9e315-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="9e315-107">ParamArray bildirme</span><span class="sxs-lookup"><span data-stu-id="9e315-107">Declaring a ParamArray</span></span>  

 <span data-ttu-id="9e315-108">Parametre listesinde bir parametre dizisini göstermek için [ParamArray](../../../language-reference/modifiers/paramarray.md) anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9e315-108">You use the [ParamArray](../../../language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="9e315-109">Aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="9e315-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="9e315-110">Bir yordam yalnızca bir parametre dizisi tanımlayabilir ve yordam tanımındaki son parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e315-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="9e315-111">Parametre dizisinin değere göre geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e315-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="9e315-112">Yordam tanımına [ByVal](../../../language-reference/modifiers/byval.md) anahtar sözcüğünü açıkça eklemek iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="9e315-112">It is good programming practice to explicitly include the [ByVal](../../../language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="9e315-113">Parametre dizisi otomatik olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e315-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="9e315-114">Varsayılan değeri, parametre dizisinin öğe türünün boş bir boyutlu dizisidir.</span><span class="sxs-lookup"><span data-stu-id="9e315-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="9e315-115">Parametre dizisinin önceki tüm parametreleri gerekli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e315-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="9e315-116">Parametre dizisi, tek bir isteğe bağlı parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e315-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="9e315-117">ParamArray çağırma</span><span class="sxs-lookup"><span data-stu-id="9e315-117">Calling a ParamArray</span></span>  

 <span data-ttu-id="9e315-118">Bir parametre dizisini tanımlayan bir yordamı çağırdığınızda, bağımsız değişkenini aşağıdaki yöntemlerle sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e315-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="9e315-119">Nothing — Yani, [ParamArray](../../../language-reference/modifiers/paramarray.md) bağımsız değişkenini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e315-119">Nothing — that is, you can omit the [ParamArray](../../../language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="9e315-120">Bu durumda, yordama boş bir dizi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9e315-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="9e315-121">[Nothing](../../../language-reference/nothing.md) anahtar sözcüğünü açıkça geçirirseniz, yordama bir null dizi geçirilir ve çağrılan yordam bu koşulu Denetmezse bir NullReferenceException öğesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e315-121">If you explicitly pass the [Nothing](../../../language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.</span></span>
  
- <span data-ttu-id="9e315-122">Virgülle ayırarak rastgele sayıda bağımsız değişken listesi.</span><span class="sxs-lookup"><span data-stu-id="9e315-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="9e315-123">Her bağımsız değişkenin veri türü, örtülü olarak öğe türüne dönüştürülebilir olmalıdır `ParamArray` .</span><span class="sxs-lookup"><span data-stu-id="9e315-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="9e315-124">Parametre dizisinin öğe türüyle aynı öğe türüne sahip bir dizi.</span><span class="sxs-lookup"><span data-stu-id="9e315-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="9e315-125">Her durumda, yordam içindeki kod parametre dizisini, veri türüyle aynı veri türü öğeleriyle tek boyutlu bir dizi olarak değerlendirir `ParamArray` .</span><span class="sxs-lookup"><span data-stu-id="9e315-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9e315-126">Süresiz olarak büyük olabilecek bir dizi ile uğraşmanız durumunda, uygulamanızın bazı iç kapasitesini çok fazla çalıştırmaya yönelik bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="9e315-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="9e315-127">Bir parametre dizisini kabul ediyorsanız, çağıran kodun kendisine geçirildiği dizinin boyutunu test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="9e315-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="9e315-128">Uygulamanız için çok büyükse uygun adımları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9e315-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="9e315-129">Daha fazla bilgi için bkz. [diziler](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e315-129">For more information, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e315-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e315-130">Example</span></span>  

 <span data-ttu-id="9e315-131">Aşağıdaki örnek, işlevini tanımlar ve çağırır `calcSum` .</span><span class="sxs-lookup"><span data-stu-id="9e315-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="9e315-132">`ParamArray`Parametresi için değiştirici, `args` işlevin değişken sayıda bağımsız değişken kabul etmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e315-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="9e315-133">Aşağıdaki örnek, bir parametre dizisi ile bir yordam tanımlar ve parametre dizisine geçirilen tüm dizi öğelerinin değerlerini çıkarır.</span><span class="sxs-lookup"><span data-stu-id="9e315-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="9e315-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e315-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="9e315-135">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9e315-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9e315-136">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9e315-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9e315-137">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9e315-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="9e315-138">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9e315-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="9e315-139">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e315-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="9e315-140">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="9e315-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="9e315-141">Diziler</span><span class="sxs-lookup"><span data-stu-id="9e315-141">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="9e315-142">İsteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="9e315-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
