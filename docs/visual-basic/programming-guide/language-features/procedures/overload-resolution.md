---
title: Aşırı Yükleme Çözümü (Visual Basic Başvurusu)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e62560d853c95bc4bba6ba829d8579ee4388858e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="504d0-102">Aşırı Yükleme Çözümü (Visual Basic Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="504d0-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="504d0-103">Visual Basic derleyici birden fazla aşırı yüklenmiş sürümlerde tanımlı bir yordam çağrısına karşılaştığında derleyici çağırmak için aşırı hangisinin karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="504d0-103">When the Visual Basic compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="504d0-104">Bunu aşağıdaki adımları gerçekleştirerek yapar:</span><span class="sxs-lookup"><span data-stu-id="504d0-104">It does this by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="504d0-105">**Erişilebilirlik.**</span><span class="sxs-lookup"><span data-stu-id="504d0-105">**Accessibility.**</span></span> <span data-ttu-id="504d0-106">Bu, çağrıyı yapan kod çağırma sonucu engelleyen bir erişim düzeyi ile hiçbir aşırı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="504d0-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2.  <span data-ttu-id="504d0-107">**Parametre sayısı.**</span><span class="sxs-lookup"><span data-stu-id="504d0-107">**Number of Parameters.**</span></span> <span data-ttu-id="504d0-108">Bu, farklı sayıda parametreleri çağrısında sağlanan daha tanımlar hiçbir aşırı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="504d0-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3.  <span data-ttu-id="504d0-109">**Parametre veri türleri.**</span><span class="sxs-lookup"><span data-stu-id="504d0-109">**Parameter Data Types.**</span></span> <span data-ttu-id="504d0-110">Derleyici örneği yöntemleri tercih genişletme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="504d0-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="504d0-111">Herhangi bir örnek yöntemi yalnızca yordam çağrısı eşleşecek şekilde dönüşümleri gerektiren bulunursa, tüm genişletme yöntemleri bırakılan ve derleyici yalnızca örnek yöntem aday ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="504d0-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="504d0-112">Bu tür bir örnek yöntemi bulunursa, örneği ve genişletme yöntemleri ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="504d0-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="504d0-113">Bu adımda, kendisi için arama bağımsız değişkenlerinin veri türlerini aşırı tanımlanan parametre türleri dönüştürülemez hiçbir aşırı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="504d0-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4.  <span data-ttu-id="504d0-114">**Daraltma dönüşümleri.**</span><span class="sxs-lookup"><span data-stu-id="504d0-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="504d0-115">Bu arama bağımsız değişken türleri daraltma dönüştürme tanımlanan parametre türleri için gerektiren hiçbir aşırı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="504d0-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="504d0-116">Bu tür denetlemesi olup geçiş geçerlidir ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `On` veya `Off`.</span><span class="sxs-lookup"><span data-stu-id="504d0-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5.  <span data-ttu-id="504d0-117">**En az genişletme.**</span><span class="sxs-lookup"><span data-stu-id="504d0-117">**Least Widening.**</span></span> <span data-ttu-id="504d0-118">Derleyici çiftleri içinde kalan aşırı göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="504d0-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="504d0-119">Her çifti için tanımlanan parametrelerin veri türlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="504d0-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="504d0-120">Karşılık gelen türlerine diğer tüm aşırı türlerinde genişletmek, derleyici ikinci ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="504d0-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="504d0-121">Diğer bir deyişle, en az genişletme miktarını gerektirir aşırı korur.</span><span class="sxs-lookup"><span data-stu-id="504d0-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6.  <span data-ttu-id="504d0-122">**Tek adayı.**</span><span class="sxs-lookup"><span data-stu-id="504d0-122">**Single Candidate.**</span></span> <span data-ttu-id="504d0-123">Aşırı çiftler halinde tek kadar kalır aşırı yükleme ve bu aşırı çağrısı çözümler considering devam eder.</span><span class="sxs-lookup"><span data-stu-id="504d0-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="504d0-124">Derleyici tek bir aday için aşırı indiremezsiniz bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="504d0-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="504d0-125">Aşağıdaki çizimde çağırmak için aşırı yüklü sürümlerini kümesinin belirleyen işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="504d0-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="504d0-126">![Aşırı çözümleme işlemi Akış Diyagramı](./media/overloadres.gif "OverloadRes")</span><span class="sxs-lookup"><span data-stu-id="504d0-126">![Flow diagram of overload resolution process](./media/overloadres.gif "OverloadRes")</span></span>  
<span data-ttu-id="504d0-127">Aşırı yüklenmiş sürümleri arasında çözme</span><span class="sxs-lookup"><span data-stu-id="504d0-127">Resolving among overloaded versions</span></span>  
  
 <span data-ttu-id="504d0-128">Aşağıdaki örnek, bu aşırı çözümleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="504d0-128">The following example illustrates this overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 <span data-ttu-id="504d0-129">İlk çağrıda derleyici ilk aşırı çünkü ortadan kaldıran ilk bağımsız değişken türü (`Short`) daraltır karşılık gelen parametrenin türünü (`Byte`).</span><span class="sxs-lookup"><span data-stu-id="504d0-129">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="504d0-130">Tür bağımsız değişkeni, her olduğundan ikinci aşırı sonra üçüncü aşırı ortadan (`Short` ve `Single`) üçüncü aşırı içinde karşılık gelen türüne widens (`Integer` ve `Single`).</span><span class="sxs-lookup"><span data-stu-id="504d0-130">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="504d0-131">Böylece isteğe bağlı olarak derleyici çağrısı kullanır ikinci aşırı daha az genişletme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="504d0-131">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="504d0-132">İkinci çağrıda derleyici daraltma temel alarak aşırı hiçbirini ortadan olamaz.</span><span class="sxs-lookup"><span data-stu-id="504d0-132">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="504d0-133">Daha az bağımsız değişken türleri genişletme ile ikinci aşırı çağırabilirsiniz olduğundan, üçüncü aşırı ilk çağrıda olduğu gibi aynı nedenden dolayı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="504d0-133">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="504d0-134">Ancak, derleyici arasında birinci ve ikinci aşırı yüklemeleri çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="504d0-134">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="504d0-135">Her karşılık gelen türü diğer widens bir tanımlanan parametre türüne sahip (`Byte` için `Short`, ancak `Single` için `Double`).</span><span class="sxs-lookup"><span data-stu-id="504d0-135">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="504d0-136">Derleyici, bu nedenle bir aşırı yüklemesini çözümleme hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="504d0-136">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="504d0-137">İsteğe bağlı aşırı ve ParamArray bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="504d0-137">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="504d0-138">Bir yordamın iki aşırı son parametre bildirilmiş dışında aynı imzaları varsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) birinde ve [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) diğer, bu yordamı yapılan bir çağrı derleyici çözümler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="504d0-138">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="504d0-139">Çağrı son bağımsız değişken olarak sağlarsa</span><span class="sxs-lookup"><span data-stu-id="504d0-139">If the call supplies the last argument as</span></span>|<span data-ttu-id="504d0-140">Son bağımsız değişken olarak bildirme aşırı çağrısı derleyici çözümler</span><span class="sxs-lookup"><span data-stu-id="504d0-140">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="504d0-141">Herhangi bir değer (atlanmış bağımsız değişkeni)</span><span class="sxs-lookup"><span data-stu-id="504d0-141">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="504d0-142">tek bir değer</span><span class="sxs-lookup"><span data-stu-id="504d0-142">A single value</span></span>|`Optional`|  
|<span data-ttu-id="504d0-143">Virgülle ayrılmış bir liste iki veya daha fazla değer</span><span class="sxs-lookup"><span data-stu-id="504d0-143">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="504d0-144">(Boş bir dizi dahil) herhangi bir uzunlukta bir dizi</span><span class="sxs-lookup"><span data-stu-id="504d0-144">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="504d0-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="504d0-145">See Also</span></span>  
 [<span data-ttu-id="504d0-146">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="504d0-146">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="504d0-147">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="504d0-147">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="504d0-148">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="504d0-148">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="504d0-149">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="504d0-149">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="504d0-150">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="504d0-150">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="504d0-151">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="504d0-151">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="504d0-152">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="504d0-152">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="504d0-153">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="504d0-153">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="504d0-154">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="504d0-154">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="504d0-155">Overloads</span><span class="sxs-lookup"><span data-stu-id="504d0-155">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="504d0-156">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="504d0-156">Extension Methods</span></span>](./extension-methods.md)
