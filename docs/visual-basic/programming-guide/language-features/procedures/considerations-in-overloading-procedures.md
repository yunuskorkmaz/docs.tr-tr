---
title: Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: f14cc28960af28530bda9a78c1309dea10c18b8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815602"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="7aae7-102">Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aae7-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="7aae7-103">Bir yordamı aşırı yükleme, farklı bir kullanmalısınız *imza* aşırı yüklü her sürüm için.</span><span class="sxs-lookup"><span data-stu-id="7aae7-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="7aae7-104">Bu, genellikle her sürüm başka bir parametre listesi belirtmelisiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="7aae7-105">Daha fazla bilgi için bkz: "Farklı imza" [yordam aşırı yüklemesi](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="7aae7-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="7aae7-106">Aşırı yüklenme olabilir bir `Function` yordamla bir `Sub` yordamı ve bunun tersi de farklı imzalara sahip oldukları sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7aae7-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="7aae7-107">İki aşırı yüklemesi, yalnızca bir dönüş değeri varsa ve diğer yok farklılık göstermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="7aae7-108">Bir yordamı aşırı yükleme aynı şekilde bir özelliği aşırı yükleyebilirsiniz ve aynı kısıtlamalara sahip.</span><span class="sxs-lookup"><span data-stu-id="7aae7-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="7aae7-109">Bir yordamı aşırı yükleme olamaz ancak, bir özellik veya bunun tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="7aae7-110">Aşırı yüklenmiş sürümleri alternatifleri</span><span class="sxs-lookup"><span data-stu-id="7aae7-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="7aae7-111">Özellikle isteğe bağlı bağımsız değişkenler varlığını veya numarasına değişkeni bazen aşırı yüklenmiş sürümleri seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="7aae7-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="7aae7-112">İsteğe bağlı bağımsız değişkenlere mutlaka tüm diller tarafından desteklenmez ve Visual Basic parametre dizileri sınırlıdır aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7aae7-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="7aae7-113">Birkaç farklı dildeki hiçbirinde yazılan kodundan çağrılmak büyük olasılıkla bir yordam yazıyorsanız, en büyük esnekliği sürümleri teklif aşırı.</span><span class="sxs-lookup"><span data-stu-id="7aae7-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="7aae7-114">İsteğe bağlı bağımsız değişkenler ve aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="7aae7-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="7aae7-115">Çağıran kod, isteğe bağlı olarak sağlamak veya bir veya daha fazla bağımsız değişken çıkarın, birden fazla aşırı yüklü sürümler tanımlayın veya isteğe bağlı parametreler kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aae7-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="7aae7-116">Ne zaman aşırı yüklenmiş sürümleri kullanın</span><span class="sxs-lookup"><span data-stu-id="7aae7-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="7aae7-117">Aşağıdaki durumlarda bir dizi aşırı yüklü sürümlerini tanımlama düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7aae7-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="7aae7-118">Yordam kodunda mantığı olup çağrıldığı koda bir isteğe bağlı bağımsız değişkeni veya sağlar bağlı olarak önemli ölçüde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="7aae7-119">Yordam kodu güvenilir bir şekilde çağıran kod tarafından sağlanan bağımsız değişken isteğe bağlı olup olmadığını test edilemez.</span><span class="sxs-lookup"><span data-stu-id="7aae7-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="7aae7-120">Bu durumda, yoksa hiçbir olası aday varsayılan bir değer için örneğin, çağıran kodun sağlamak için beklenebilir değil.</span><span class="sxs-lookup"><span data-stu-id="7aae7-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="7aae7-121">Olduğunda isteğe bağlı parametreler kullanılacak</span><span class="sxs-lookup"><span data-stu-id="7aae7-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="7aae7-122">Bir veya daha fazla isteğe bağlı parametreler aşağıdaki durumlarda tercih edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7aae7-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="7aae7-123">Çağıran kod, isteğe bağlı bağımsız değişken sağlamıyor çalıştırıldığında yalnızca gerekli eylem parametresi varsayılan değerine ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7aae7-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="7aae7-124">Bir veya daha fazla tek bir sürüm tanımlarsanız, böyle bir durumda yordamının kodunu daha az karmaşık olabilir `Optional` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7aae7-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="7aae7-125">Daha fazla bilgi için [isteğe bağlı parametreler](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7aae7-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="7aae7-126">ParamArrays ve aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="7aae7-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="7aae7-127">Çağıran kod, değişken sayıda bağımsız değişken geçirebilirsiniz, birden fazla aşırı yüklü sürümler tanımlayın veya bir parametre dizisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aae7-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="7aae7-128">Ne zaman aşırı yüklenmiş sürümleri kullanın</span><span class="sxs-lookup"><span data-stu-id="7aae7-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="7aae7-129">Aşağıdaki durumlarda bir dizi aşırı yüklü sürümlerini tanımlama düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7aae7-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="7aae7-130">Çağıran kod hiçbir zaman birden çok az sayıda değerler için parametre dizisi geçen biliyor.</span><span class="sxs-lookup"><span data-stu-id="7aae7-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="7aae7-131">Yordam kodunda mantığı çağıran kod geçirir kaç değerlerine bağlı olarak önemli ölçüde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="7aae7-132">Çağıran kod, farklı veri türleri değerlerinin geçmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aae7-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="7aae7-133">Ne zaman bir parametre dizisi kullanılır?</span><span class="sxs-lookup"><span data-stu-id="7aae7-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="7aae7-134">Daha iyi tarafından sunulan bir `ParamArray` parametre aşağıdaki durumlarda:</span><span class="sxs-lookup"><span data-stu-id="7aae7-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="7aae7-135">Çağıran kod için parametre dizisi geçirebilirsiniz kaç değer tahmin etmek mümkün değildir ve büyük bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="7aae7-136">Yordam mantıksal kendisini çağıran kod geçirir, her değer esas olarak aynı işlemleri gerçekleştirmek tüm değerleri üzerinden yineleme için uygundur.</span><span class="sxs-lookup"><span data-stu-id="7aae7-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="7aae7-137">Daha fazla bilgi için [parametre dizileri](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="7aae7-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="7aae7-138">İsteğe bağlı parametreler için örtük aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="7aae7-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="7aae7-139">Bir yordamı bir [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametresi, bir isteğe bağlı parametre içeren ve olmadan bir tane olmak üzere iki aşırı yüklenmiş yordam eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="7aae7-140">Bunlardan biri için karşılık gelen bir parametre listesi ile bu tür bir yordamı aşırı yükleme yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="7aae7-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="7aae7-141">Aşağıdaki bildirimleri bu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="7aae7-142">Birden fazla isteğe bağlı parametre içeren bir yordam için örtük aşırı yüklemeleri, önceki örnekte benzer mantığı tarafından gelen bir dizi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7aae7-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="7aae7-143">Bir ParamArray parametresiyle için örtük aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="7aae7-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="7aae7-144">Derleyici bir yordama göz önünde bulundurur bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) ne çağıran kod parametre dizisine gibi geçirir birbirinden farklı aşırı yüklemeler, sonsuz bir sayıda parametre:</span><span class="sxs-lookup"><span data-stu-id="7aae7-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="7aae7-145">Ne zaman çağıran kodu bir bağımsız değişken sağlamıyor için bir aşırı yükleme `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="7aae7-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="7aae7-146">Çağıran kod tek boyutlu bir dizi zaman kaynakları için bir aşırı `ParamArray` öğe türü</span><span class="sxs-lookup"><span data-stu-id="7aae7-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="7aae7-147">Her bir pozitif tamsayı için bir aşırı yükleme için çağıran kod sağlar, her biri bağımsız değişken sayısı olduğunda `ParamArray` öğe türü</span><span class="sxs-lookup"><span data-stu-id="7aae7-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="7aae7-148">Aşağıdaki bildirimleri bu örtük aşırı yüklemeler göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="7aae7-149">Böyle bir yordam bir parametre listesiyle parametre dizisi için tek boyutlu bir dizi alan aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="7aae7-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="7aae7-150">Ancak, bir örtük aşırı imzalarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aae7-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="7aae7-151">Aşağıdaki bildirimleri bu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="7aae7-152">Aşırı yükleme alternatif olarak yazısız programlama</span><span class="sxs-lookup"><span data-stu-id="7aae7-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="7aae7-153">Farklı veri türleri için bir parametre geçirmek çağıran kod izin vermek istiyorsanız, alternatif bir yaklaşım yazısız programlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="7aae7-154">Tür denetleme anahtara ayarlayabilirsiniz `Off` ya da ile [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) veya [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7aae7-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="7aae7-155">Ardından parametrenin veri türü bildirmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7aae7-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="7aae7-156">Ancak, bu yaklaşım, aşırı yüklemesi için kıyasla aşağıdaki dezavantajları bulunur:</span><span class="sxs-lookup"><span data-stu-id="7aae7-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="7aae7-157">Yazısız programlama yürütme daha az verimli kod üretir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-157">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="7aae7-158">Yordamı, geçirilen düşünmektedir her veri türü için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7aae7-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="7aae7-159">Derleyici çağıran kod yordamı desteklemediği bir veri türü geçerse hata sinyali vermek olamaz.</span><span class="sxs-lookup"><span data-stu-id="7aae7-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aae7-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7aae7-160">See also</span></span>

- [<span data-ttu-id="7aae7-161">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="7aae7-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7aae7-162">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="7aae7-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7aae7-163">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="7aae7-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="7aae7-164">Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="7aae7-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="7aae7-165">Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="7aae7-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="7aae7-166">Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="7aae7-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="7aae7-167">Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="7aae7-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="7aae7-168">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="7aae7-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="7aae7-169">Overloads</span><span class="sxs-lookup"><span data-stu-id="7aae7-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
