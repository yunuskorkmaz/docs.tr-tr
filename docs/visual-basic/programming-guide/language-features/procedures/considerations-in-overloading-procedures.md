---
title: Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac4bc47f9e781f83c7930efffedd40d9c25c2ec2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="2060c-102">Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2060c-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="2060c-103">Bir yordamı aşırı yükleme, farklı bir kullanmalısınız *imza* aşırı yüklenmiş her sürüm için.</span><span class="sxs-lookup"><span data-stu-id="2060c-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="2060c-104">Bu, genellikle her sürümü farklı parametre listesi belirtmelisiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2060c-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="2060c-105">Daha fazla bilgi için bkz: "Farklı imza" [yordam aşırı yüklemesi](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="2060c-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="2060c-106">Aşırı yüklenebilir bir `Function` yordamla bir `Sub` yordamı ve bunun tersini yapmak, sahip oldukları farklı imzalar sağlanan.</span><span class="sxs-lookup"><span data-stu-id="2060c-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="2060c-107">İki aşırı yalnızca bir dönüş değeri varsa ve diğer desteklemez, farklı olamaz.</span><span class="sxs-lookup"><span data-stu-id="2060c-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="2060c-108">Bir yordamı aşırı yükleme aynı şekilde bir özellik aşırı yüklenebilir ve aynı kısıtlamalara sahip.</span><span class="sxs-lookup"><span data-stu-id="2060c-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="2060c-109">Bir yordamı aşırı yükleme olamaz ancak, bir özellik veya tersi.</span><span class="sxs-lookup"><span data-stu-id="2060c-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="2060c-110">Aşırı yüklenmiş sürümleri alternatifleri</span><span class="sxs-lookup"><span data-stu-id="2060c-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="2060c-111">Özellikle bağımsız değişken varlığını isteğe bağlı olduğunda veya numarasına değişkenidir bazen aşırı yüklenmiş sürümlere seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="2060c-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="2060c-112">İsteğe bağlı bağımsız değişkenler mutlaka tüm diller tarafından desteklenmez ve parametre dizileri Visual Basic'e sınırlı aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2060c-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="2060c-113">Birkaç farklı dildeki hiçbirinde yazılan kod öğesinden çağrılması büyük olasılıkla bir yordam yazıyorsanız sürümleri teklif en büyük esnekliği aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="2060c-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="2060c-114">Aşırı ve isteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2060c-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="2060c-115">Çağrıyı yapan kod, isteğe bağlı olarak sağlayın veya bağımsız değişkenlerden biri veya daha fazla atlarsanız, birden çok aşırı yüklü sürümlerini tanımlamak veya isteğe bağlı parametreler kullanın.</span><span class="sxs-lookup"><span data-stu-id="2060c-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="2060c-116">Ne zaman kullanılacağı sürümleri aşırı yüklenmiş</span><span class="sxs-lookup"><span data-stu-id="2060c-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="2060c-117">Aşağıdaki durumlarda aşırı yüklenmiş sürümlerinin bir dizi tanımlamayı düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2060c-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="2060c-118">Yordam kodu mantık olup çağıran kodu isteğe bağlı bir bağımsız değişken veya sağlayan bağlı olarak önemli ölçüde farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2060c-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="2060c-119">Çağıran kodu isteğe bağlı bir bağımsız değişken sağlanan olup olmadığını yordamı kodu güvenilir bir şekilde test edilemez.</span><span class="sxs-lookup"><span data-stu-id="2060c-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="2060c-120">Bu durumda, yoksa hiçbir olası adayı varsayılan bir değer için örneğin, çağrıyı yapan kod sağlamak için beklenebilir değil.</span><span class="sxs-lookup"><span data-stu-id="2060c-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="2060c-121">Ne zaman isteğe bağlı parametreler kullanılır</span><span class="sxs-lookup"><span data-stu-id="2060c-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="2060c-122">Bir veya daha fazla isteğe bağlı parametreler aşağıdaki durumlarda tercih edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2060c-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="2060c-123">Çağrıyı yapan kod isteğe bağlı bir bağımsız değişken sağlayın değil, yalnızca gerekli parametre için varsayılan bir değer ayarlamak için eylemdir.</span><span class="sxs-lookup"><span data-stu-id="2060c-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="2060c-124">Bir veya daha fazla tek sürümü tanımlarsanız, böyle bir durumda yordamı kod daha az karmaşık olabilir `Optional` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="2060c-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="2060c-125">Daha fazla bilgi için bkz: [isteğe bağlı parametreler](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2060c-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="2060c-126">Aşırı ve ParamArrays</span><span class="sxs-lookup"><span data-stu-id="2060c-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="2060c-127">Çağıran kodu değişken sayıda bağımsız değişken geçirdiğinizde birden çok aşırı yüklü sürümlerini tanımlamak ya da bir parametre dizisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="2060c-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="2060c-128">Ne zaman kullanılacağı sürümleri aşırı yüklenmiş</span><span class="sxs-lookup"><span data-stu-id="2060c-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="2060c-129">Aşağıdaki durumlarda aşırı yüklenmiş sürümlerinin bir dizi tanımlamayı düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2060c-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="2060c-130">Çağrıyı yapan kod hiçbir zaman birden çok az sayıda değerleri parametre dizisine geçtiğini bildiğiniz.</span><span class="sxs-lookup"><span data-stu-id="2060c-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="2060c-131">Yordam kodu mantık çağıran kodu geçirir kaç değerleri bağlı olarak önemli ölçüde farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2060c-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="2060c-132">Çağrıyı yapan kod farklı veri türlerini değerlerinin geçmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2060c-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="2060c-133">Bir parametre dizisi kullanma zamanı</span><span class="sxs-lookup"><span data-stu-id="2060c-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="2060c-134">Daha iyi tarafından sunulan bir `ParamArray` aşağıdaki durumlarda parametre:</span><span class="sxs-lookup"><span data-stu-id="2060c-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="2060c-135">Çağrıyı yapan kod parametre dizisine geçirebilirsiniz kaç değerleri tahmin etmek mümkün değildir ve büyük bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2060c-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="2060c-136">Yordam mantığı kendisini çağıran kodu geçirir, her değer üzerinde temelde aynı işlemler tüm değerler üzerinden yineleme için uygundur.</span><span class="sxs-lookup"><span data-stu-id="2060c-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="2060c-137">Daha fazla bilgi için bkz: [parametre dizileri](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="2060c-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="2060c-138">İsteğe bağlı parametreler için örtük aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="2060c-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="2060c-139">Bir yordama bir [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametresi, bir isteğe bağlı bir parametre ve olmadan bir olmak üzere iki aşırı yüklenmiş yordamları eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2060c-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="2060c-140">Bunlardan birisi karşılık gelen bir parametre listesi ile bu tür bir yordamı aşırı yükleme yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2060c-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="2060c-141">Aşağıdaki bildirimler bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2060c-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 <span data-ttu-id="2060c-142">Birden fazla isteğe bağlı bir parametre ile bir yordam için örtük aşırı yüklemeleri, önceki örnekte benzer mantığı tarafından gelen kümesi yok.</span><span class="sxs-lookup"><span data-stu-id="2060c-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="2060c-143">ParamArray parametresi için örtük aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="2060c-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="2060c-144">Bir yordama derleyici göz önünde bulundurur bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) ne çağıran kodu parametre dizisine gibi geçirir birbirinden farklı bir aşırı yüklemeleri, sonsuz sayıda sahip parametre:</span><span class="sxs-lookup"><span data-stu-id="2060c-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="2060c-145">Ne zaman çağıran kodu bir bağımsız değişken sağlamıyor için aşırı yüklemesiyle `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="2060c-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="2060c-146">Ne zaman tek boyutlu dizi çağıran kodu sağlıyor için aşırı yüklemesiyle `ParamArray` öğe türü</span><span class="sxs-lookup"><span data-stu-id="2060c-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="2060c-147">Her bir pozitif tamsayı için bir aşırı yükleme için bu bağımsız değişken sayısı, her biri çağıran kodu sağlıyor zaman `ParamArray` öğe türü</span><span class="sxs-lookup"><span data-stu-id="2060c-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="2060c-148">Aşağıdaki bildirimler bu örtük aşırı yüklemeleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2060c-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 <span data-ttu-id="2060c-149">Tek boyutlu bir dizi parametre dizisi için gereken bir parametre listesi ile bu tür bir yordamı aşırı yükleme yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2060c-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="2060c-150">Ancak, diğer örtük aşırı imzalarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2060c-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="2060c-151">Aşağıdaki bildirimler bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2060c-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="2060c-152">Aşırı yükleme alternatif olarak yazısız programlama</span><span class="sxs-lookup"><span data-stu-id="2060c-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="2060c-153">Veri türleri farklı bir parametreye geçirmek üzere çağıran kodu izin vermek istiyorsanız, alternatif bir yaklaşım yazısız programlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="2060c-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="2060c-154">Tür anahtara denetleme ayarlayabilirsiniz `Off` ya da ile [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) veya [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2060c-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="2060c-155">Ardından parametre veri türü belirtmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2060c-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="2060c-156">Ancak, bu yaklaşım aşırı yüklemesi için kıyasla aşağıdaki dezavantajları bulunur:</span><span class="sxs-lookup"><span data-stu-id="2060c-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="2060c-157">Yazısız programlama daha az verimli yürütme kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2060c-157">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="2060c-158">Yordam geçirilen düşünmektedir her veri türü için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2060c-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="2060c-159">Derleyici arama kodu yordamı desteği olmayan bir veri türü geçirir, bir hata sinyal olamaz.</span><span class="sxs-lookup"><span data-stu-id="2060c-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2060c-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2060c-160">See Also</span></span>  
 [<span data-ttu-id="2060c-161">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2060c-161">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="2060c-162">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="2060c-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="2060c-163">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="2060c-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="2060c-164">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="2060c-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="2060c-165">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="2060c-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="2060c-166">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="2060c-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="2060c-167">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="2060c-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="2060c-168">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="2060c-168">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="2060c-169">Overloads</span><span class="sxs-lookup"><span data-stu-id="2060c-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
