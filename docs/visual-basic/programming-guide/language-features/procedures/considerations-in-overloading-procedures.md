---
description: 'Daha fazla bilgi edinin: ek yükleme yordamlarındaki konular (Visual Basic)'
title: Yordamları Aşırı Yüklemeye İlişkin Düşünceler
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
ms.openlocfilehash: ee6dc0ce23f0706f52ac58673d37d1b72936d2bc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472624"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="8d79d-103">Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d79d-103">Considerations in Overloading Procedures (Visual Basic)</span></span>

<span data-ttu-id="8d79d-104">Bir yordamı aşırı yüklerken, her aşırı yüklenmiş sürüm için farklı bir *imza* kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-104">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="8d79d-105">Bu genellikle her sürümün farklı bir parametre listesi belirtmesi gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-105">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="8d79d-106">Daha fazla bilgi için [yordam aşırı](./procedure-overloading.md)yüklemesinde "farklı imza" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="8d79d-106">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="8d79d-107">Yordamı `Function` `Sub` farklı imzaya sahip olmaları kaydıyla, prosedürü bir yordam ile aşırı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-107">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="8d79d-108">İki aşırı yükleme yalnızca, bir dönüş değerine sahip ve diğeri değil ' de farklı olamaz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-108">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="8d79d-109">Bir özelliği, bir yordamı aşırı yükle aynı şekilde ve aynı kısıtlamalara sahip olacak şekilde aşırı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-109">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="8d79d-110">Ancak, bir yordamı özellik ile aşırı yükleyemez veya tam tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-110">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="8d79d-111">Aşırı yüklenmiş sürümlerin alternatifleri</span><span class="sxs-lookup"><span data-stu-id="8d79d-111">Alternatives to Overloaded Versions</span></span>  

 <span data-ttu-id="8d79d-112">Bazen, özellikle bağımsız değişkenlerin varlığı isteğe bağlı olduğunda veya bu sayının değişken olduğu durumlarda aşırı yüklenmiş sürümlerin alternatifleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8d79d-112">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="8d79d-113">İsteğe bağlı bağımsız değişkenlerin tüm diller tarafından desteklenmeyeceğini ve parametre dizilerinin Visual Basic sınırlı olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8d79d-113">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="8d79d-114">Birçok farklı dilde yazılmış koddan çağrılabilir olabilecek bir yordam yazıyorsanız, aşırı yüklenmiş sürümler en büyük esnekliği sunar.</span><span class="sxs-lookup"><span data-stu-id="8d79d-114">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="8d79d-115">Aşırı yüklemeler ve Isteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8d79d-115">Overloads and Optional Arguments</span></span>  

 <span data-ttu-id="8d79d-116">Çağıran kod isteğe bağlı olarak bir veya daha fazla bağımsız değişken sağlayabilir ya da atlayabilir, birden fazla aşırı yüklü sürümü tanımlayabilir veya isteğe bağlı parametreleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-116">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="8d79d-117">Aşırı yüklenmiş sürümlerin ne zaman kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="8d79d-117">When to Use Overloaded Versions</span></span>  

 <span data-ttu-id="8d79d-118">Aşağıdaki durumlarda aşırı yüklenmiş bir dizi sürümü tanımlamayı düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d79d-118">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="8d79d-119">Yordam kodundaki mantık, çağıran kodun isteğe bağlı bir bağımsız değişken olmasına bağlı olarak önemli ölçüde farklılık gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="8d79d-119">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="8d79d-120">Yordam kodu, çağıran kodun isteğe bağlı bir bağımsız değişken sağlayıp sağlamadığını güvenilir bir şekilde test edemez.</span><span class="sxs-lookup"><span data-stu-id="8d79d-120">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="8d79d-121">Bu durum, örneğin, çağıran kodun sağlaması beklenmediği bir varsayılan değer için olası bir aday yoksa olur.</span><span class="sxs-lookup"><span data-stu-id="8d79d-121">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="8d79d-122">Isteğe bağlı parametrelerin ne zaman kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="8d79d-122">When to Use Optional Parameters</span></span>  

 <span data-ttu-id="8d79d-123">Aşağıdaki durumlarda bir veya daha fazla isteğe bağlı parametre tercih edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d79d-123">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="8d79d-124">Çağıran kod için isteğe bağlı bir bağımsız değişken sağlamadan yalnızca gerekli olan eylem, parametreyi varsayılan bir değere ayarlayamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d79d-124">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="8d79d-125">Böyle bir durumda, bir veya daha fazla parametre içeren tek bir sürüm tanımlarsanız yordam kodu daha karmaşık olabilir `Optional` .</span><span class="sxs-lookup"><span data-stu-id="8d79d-125">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="8d79d-126">Daha fazla bilgi için bkz. [Isteğe bağlı parametreler](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8d79d-126">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="8d79d-127">Aşırı yüklemeler ve ParamArrays</span><span class="sxs-lookup"><span data-stu-id="8d79d-127">Overloads and ParamArrays</span></span>  

 <span data-ttu-id="8d79d-128">Çağıran kod, değişken sayıda bağımsız değişken geçebilirler, birden fazla aşırı yüklenmiş sürüm tanımlayabilir veya bir parametre dizisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-128">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="8d79d-129">Aşırı yüklenmiş sürümlerin ne zaman kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="8d79d-129">When to Use Overloaded Versions</span></span>  

 <span data-ttu-id="8d79d-130">Aşağıdaki durumlarda aşırı yüklenmiş bir dizi sürümü tanımlamayı düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d79d-130">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="8d79d-131">Çağıran kodun parametre dizisine çok az sayıda değerden fazlasını geçirmediğini bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-131">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="8d79d-132">Yordam kodundaki mantık, çağıran kodun kaç değere geçirdiğine bağlı olarak önemli ölçüde farklılık gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="8d79d-132">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="8d79d-133">Çağıran kod, farklı veri türlerinin değerlerini geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-133">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="8d79d-134">Parametre dizisi ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="8d79d-134">When to Use a Parameter Array</span></span>  

 <span data-ttu-id="8d79d-135">Aşağıdaki durumlarda bir parametre tarafından daha iyi hizmet verilmiştir `ParamArray` :</span><span class="sxs-lookup"><span data-stu-id="8d79d-135">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="8d79d-136">Çağıran kodun parametre dizisine kaç değer geçirebildiğini tahmin edemeyeceksiniz ve bu da büyük bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-136">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="8d79d-137">Yordamın mantığı, çağıran kodun geçtiği tüm değerlerle yinelemesine, temelde her değer üzerinde aynı işlemleri gerçekleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d79d-137">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="8d79d-138">Daha fazla bilgi için bkz. [parametre dizileri](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8d79d-138">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="8d79d-139">Isteğe bağlı parametreler için örtük aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="8d79d-139">Implicit Overloads for Optional Parameters</span></span>  

 <span data-ttu-id="8d79d-140">[Isteğe bağlı](../../../language-reference/modifiers/optional.md) parametresine sahip bir yordam, biri isteğe bağlı parametre ve diğeri olmadan olan iki aşırı yüklenmiş yordama eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-140">A procedure with an [Optional](../../../language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="8d79d-141">Bu tür bir yordamı, bunlardan birine karşılık gelen bir parametre listesi ile aşırı yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-141">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="8d79d-142">Aşağıdaki bildirimlerde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-142">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="8d79d-143">Birden fazla isteğe bağlı parametreye sahip bir yordam için, önceki örnekteki şuna benzer şekilde, mantığa göre gelen bir dizi örtük aşırı yükleme vardır.</span><span class="sxs-lookup"><span data-stu-id="8d79d-143">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="8d79d-144">ParamArray parametresi için örtük aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="8d79d-144">Implicit Overloads for a ParamArray Parameter</span></span>  

 <span data-ttu-id="8d79d-145">Derleyici, bir [ParamArray](../../../language-reference/modifiers/paramarray.md) parametresi ile bir yordamı, çağıran kodun parametre dizisine ne kadar başarılı bir şekilde (örneğin, aşağıdaki şekilde) geçirdiklerinde farklılık gösteren sınırsız sayıda aşırı yüklemeye sahip olacak şekilde değerlendirir:</span><span class="sxs-lookup"><span data-stu-id="8d79d-145">The compiler considers a procedure with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="8d79d-146">Çağıran kodun bir bağımsız değişken sağlaması için bir aşırı yüklemesi `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="8d79d-146">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="8d79d-147">Çağıran kod, öğe türünde tek boyutlu bir dizi sağladığı zaman için bir aşırı yükleme `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="8d79d-147">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="8d79d-148">Her pozitif tamsayı için, çağıran kod bu sayıda bağımsız değişken sağladığı zaman için bir aşırı yükleme, her biri `ParamArray` öğe türü</span><span class="sxs-lookup"><span data-stu-id="8d79d-148">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="8d79d-149">Aşağıdaki bildirimlerde bu örtük aşırı yüklemeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-149">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="8d79d-150">Parametre dizisi için tek boyutlu bir dizi alan bir parametre listesiyle bu tür bir yordamı aşırı yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-150">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="8d79d-151">Ancak, diğer örtük aşırı yüklemelerin imzalarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-151">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="8d79d-152">Aşağıdaki bildirimlerde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-152">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="8d79d-153">Aşırı yükleme için alternatif olarak Türsüz programlama</span><span class="sxs-lookup"><span data-stu-id="8d79d-153">Typeless Programming as an Alternative to Overloading</span></span>  

 <span data-ttu-id="8d79d-154">Çağıran kodun bir parametreye farklı veri türleri geçirmeye izin vermek istiyorsanız, alternatif bir yaklaşım türsüz bir programdır.</span><span class="sxs-lookup"><span data-stu-id="8d79d-154">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="8d79d-155">Tür denetimi anahtarını, `Off` [Strict ifadesiyle](../../../language-reference/statements/option-strict-statement.md) veya [-OptionStrict](../../../reference/command-line-compiler/optionstrict.md) derleyici seçeneğiyle olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-155">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="8d79d-156">Daha sonra parametrenin veri türünü bildirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8d79d-156">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="8d79d-157">Ancak bu yaklaşım, aşırı yükleme ile karşılaştırıldığında aşağıdaki dezavantajlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8d79d-157">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="8d79d-158">Türsüz programlama daha az verimli yürütme kodu üretir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-158">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="8d79d-159">Yordamın anticipates geçirildiği her veri türü için test olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d79d-159">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="8d79d-160">Çağıran kod, yordamın desteklemediği bir veri türünü geçerse derleyici bir hata sinyalini alamaz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-160">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d79d-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d79d-161">See also</span></span>

- [<span data-ttu-id="8d79d-162">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8d79d-162">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8d79d-163">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8d79d-163">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8d79d-164">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="8d79d-164">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="8d79d-165">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="8d79d-165">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="8d79d-166">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="8d79d-166">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="8d79d-167">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="8d79d-167">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="8d79d-168">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="8d79d-168">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="8d79d-169">Aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="8d79d-169">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="8d79d-170">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="8d79d-170">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
