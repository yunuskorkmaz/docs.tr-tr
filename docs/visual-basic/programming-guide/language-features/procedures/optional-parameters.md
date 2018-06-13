---
title: İsteğe Bağlı Parametreler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: a438455668310769c5267a6d42a2e694bb7b01dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651615"
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="964fb-102">İsteğe Bağlı Parametreler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="964fb-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="964fb-103">Bir yordam parametresinin isteğe bağlı olduğunu ve yordam çağrıldığında bu parametre için hiçbir bağımsız değişken sağlanmaması gerektiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="964fb-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="964fb-104">*İsteğe bağlı parametreler* tarafından belirtilen `Optional` yordamı tanımı bir anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="964fb-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="964fb-105">Aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="964fb-105">The following rules apply:</span></span>  
  
-   <span data-ttu-id="964fb-106">Yordam tanımındaki her isteğe bağlı parametre bir varsayılan değer belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="964fb-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
-   <span data-ttu-id="964fb-107">İsteğe bağlı parametreye ilişkin varsayılan değer bir sabit ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="964fb-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
-   <span data-ttu-id="964fb-108">Yordam tanımında isteğe bağlı parametreden sonra gelen her parametre de isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="964fb-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="964fb-109">Aşağıdaki sözdiziminde, isteğe bağlı parametresi bulunan bir yordam bildirimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="964fb-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="964fb-110">İsteğe Bağlı Parametreler İçeren Yordamları Çağırma</span><span class="sxs-lookup"><span data-stu-id="964fb-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="964fb-111">İsteğe bağlı parametre içeren bir yordamı çağırdığınızda, bağımsız değişkeni sağlayıp sağlamamayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="964fb-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="964fb-112">Bunu yapmazsanız, yordam bu parametre için bildirilen varsayılan değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="964fb-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="964fb-113">Bağımsız değişken listesinde bir veya daha fazla isteğe bağlı bağımsız değişkeni atladığınızda, bunların konumlarını işaretlemek için ardışık virgüller kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="964fb-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="964fb-114">Aşağıdaki örnek çağrı birinci ve dördüncü bağımsız değişkeni sağlamakta, ancak ikinci veya üçüncüyü sağlamamaktadır:</span><span class="sxs-lookup"><span data-stu-id="964fb-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="964fb-115">Aşağıdaki örnek birkaç çağrılar `MsgBox` işlevi.</span><span class="sxs-lookup"><span data-stu-id="964fb-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="964fb-116">`MsgBox` bir parametre ve iki isteğe bağlı parametreler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="964fb-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="964fb-117">İlk çağrıda `MsgBox` sırada üç bağımsız değişken sağlar, `MsgBox` bunları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="964fb-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="964fb-118">İkinci çağrı yalnızca gerekli bağımsız değişkeni sağlar.</span><span class="sxs-lookup"><span data-stu-id="964fb-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="964fb-119">Üçüncü ve dördüncü çağrılar, birinci ve üçüncü bağımsız değişkenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="964fb-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="964fb-120">Üçüncü çağrı bunu konuma göre ve dördüncü çağrı ise ada göre yapar.</span><span class="sxs-lookup"><span data-stu-id="964fb-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](./codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="964fb-121">İsteğe Bağlı Bağımsız Değişkenin Var Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="964fb-121">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="964fb-122">Bir yordam, verilen bir bağımsız değişkenin atlanıp atlanmadığını veya çağırma kodunun varsayılan değeri açıkça sağlayıp sağlamadığını çalışma zamanında algılayamaz.</span><span class="sxs-lookup"><span data-stu-id="964fb-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="964fb-123">Bu ayrımı yapmanız gerekiyorsa, olasılık dışı bir değeri varsayılan olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="964fb-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="964fb-124">Aşağıdaki yordam isteğe bağlı parametre tanımlar `office`ve varsayılan değerini için testleri `QJZ`, onu çağrısında çıkarıldı varsa görmek için:</span><span class="sxs-lookup"><span data-stu-id="964fb-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](./codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 <span data-ttu-id="964fb-125">İsteğe bağlı parametresi bir başvuru türü gibi ise bir `String`, kullanabileceğiniz `Nothing` varsayılan değer olarak, bu olmayan bir bağımsız değişkeni için beklenen değer sağlanır.</span><span class="sxs-lookup"><span data-stu-id="964fb-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="964fb-126">İsteğe Bağlı Parametreler ve Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="964fb-126">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="964fb-127">İsteğe bağlı parametreler içeren bir yordam tanımlamanın bir başka yolu aşırı yüklemeyi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="964fb-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="964fb-128">İsteğe bağlı tek bir parametreniz varsa, prosedürün iki aşırı yüklenmiş sürümünü (biri parametreyi kabul eden, diğeri ise parametresiz olmak üzere) tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="964fb-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="964fb-129">Bu yaklaşım, isteğe bağlı parametrelerin sayısı arttıkça daha karmaşık hale gelir.</span><span class="sxs-lookup"><span data-stu-id="964fb-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="964fb-130">Ancak avantajı, çağırma programının her bir isteğe bağlı bağımsız değişkeni sağlayıp sağlamadığından kesin emin olabilmenizdir.</span><span class="sxs-lookup"><span data-stu-id="964fb-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="964fb-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="964fb-131">See Also</span></span>  
 [<span data-ttu-id="964fb-132">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="964fb-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="964fb-133">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="964fb-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="964fb-134">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="964fb-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="964fb-135">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="964fb-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="964fb-136">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="964fb-136">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="964fb-137">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="964fb-137">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="964fb-138">Optional</span><span class="sxs-lookup"><span data-stu-id="964fb-138">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="964fb-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="964fb-139">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
