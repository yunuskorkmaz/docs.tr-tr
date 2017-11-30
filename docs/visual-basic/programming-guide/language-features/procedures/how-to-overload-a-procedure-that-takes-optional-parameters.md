---
title: "Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="886af-102">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="886af-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="886af-103">Bir veya daha fazla yordam varsa, [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametreleri örtük aşırı hiçbiriyle aşırı yüklenmiş bir sürümünü tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="886af-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="886af-104">"Daha fazla bilgi için örtük aşırı yüklemeler için isteğe bağlı parametreleri" bölümüne bakın [aşırı yükleme yordamları konuları](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="886af-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="886af-105">İsteğe bağlı bir parametre</span><span class="sxs-lookup"><span data-stu-id="886af-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="886af-106">İsteğe bağlı bir parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="886af-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="886af-107">Yazma bir `Sub` veya `Function` parametre listesinde isteğe bağlı bir parametre içeren bildirimi deyimi.</span><span class="sxs-lookup"><span data-stu-id="886af-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="886af-108">Kullanmayın `Optional` Bu aşırı yüklenmiş sürümünde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="886af-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="886af-109">Öncesinde `Sub` veya `Function` anahtar sözcüğüyle [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="886af-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="886af-110">İsteğe bağlı bağımsız değişkeni çağıran kodu sağlar, yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="886af-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="886af-111">Yordamını sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="886af-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="886af-112">İsteğe bağlı parametre parametre listesinde içermez ancak bu, ilk bildirimine aynı ikinci bir bildirim deyimi yazma.</span><span class="sxs-lookup"><span data-stu-id="886af-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="886af-113">Çağrıyı yapan kod isteğe bağlı bağımsız değişkeni sağlamaz, yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="886af-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="886af-114">Yordamını sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="886af-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="886af-115">Aşağıdaki örnekte iki aşırı yüklenmiş yordamlar ve son olarak geçersiz ve geçerli aşırı yüklenmiş sürümlerinin örnekleri eşdeğer bir dizi bir isteğe bağlı parametresi tanımlı bir yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="886af-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="886af-116">Birden çok isteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="886af-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="886af-117">Birden fazla isteğe bağlı bir parametre ile bir yordam için normalde ikiden fazla aşırı yüklenmiş sürümlerin gerekir.</span><span class="sxs-lookup"><span data-stu-id="886af-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="886af-118">Örneğin, iki isteğe bağlı parametreler vardır ve çağıran kodu sağlayın veya diğer bağımsız olarak her biri atlarsanız, dört aşırı yüklenmiş sürümlerin sağlanan bağımsız değişkenler her bir olası kombinasyonu için bir tane gerekir.</span><span class="sxs-lookup"><span data-stu-id="886af-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="886af-119">İsteğe bağlı parametrelerin sayısı arttıkça, aşırı yüklemesi karmaşıklığını artırır.</span><span class="sxs-lookup"><span data-stu-id="886af-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="886af-120">N isteğe bağlı parametreler için bazı birleşimleri sağlanan bağımsız değişkenler için kabul edilebilir değil sürece 2 gereksinim ^ N aşırı sürümleri.</span><span class="sxs-lookup"><span data-stu-id="886af-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="886af-121">Yordam yapısına bağlı mantığı netlik aşırı yüklenmiş tüm sürümleri tanımlamanın ek çaba hizalar bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="886af-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="886af-122">Birden fazla isteğe bağlı bir parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="886af-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="886af-123">Hangi sağlanan isteğe bağlı bağımsız değişkenler yordamı mantığı için kabul edilebilir birleşimleridir belirler.</span><span class="sxs-lookup"><span data-stu-id="886af-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="886af-124">İsteğe bağlı bir parametre başka bağımlıysa kabul edilebilir bir birleşimi ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="886af-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="886af-125">Örneğin, bir parametre bir eşin adını kabul eder ve başka eşinin yaş kabul eder, yaş sağladığını ancak adı atlama bağımsız değişkenler bileşimi kabul edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="886af-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="886af-126">Sağlanan isteğe bağlı bağımsız değişkenler kabul edilebilir her birleşimi için yazma bir `Sub` veya `Function` karşılık gelen parametre listesi tanımlar bildirimi deyimi.</span><span class="sxs-lookup"><span data-stu-id="886af-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="886af-127">Kullanmayın `Optional` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="886af-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="886af-128">Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğüyle [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="886af-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="886af-129">Her bildirim çağrıyı yapan kod bildirim ait parametre listesine karşılık gelen bir bağımsız değişken listesi sağlar, yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="886af-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="886af-130">Her bir yordam ile sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="886af-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886af-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="886af-131">See Also</span></span>  
 [<span data-ttu-id="886af-132">Yordamları</span><span class="sxs-lookup"><span data-stu-id="886af-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="886af-133">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="886af-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="886af-134">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="886af-134">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="886af-135">Parametre dizileri</span><span class="sxs-lookup"><span data-stu-id="886af-135">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="886af-136">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="886af-136">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="886af-137">Sorun giderme yordamları</span><span class="sxs-lookup"><span data-stu-id="886af-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="886af-138">Nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="886af-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="886af-139">Nasıl yapılır: aşırı yüklenmiş bir yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="886af-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="886af-140">Nasıl yapılır: belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="886af-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="886af-141">Aşırı yükleme çözümü</span><span class="sxs-lookup"><span data-stu-id="886af-141">Overload Resolution</span></span>](./overload-resolution.md)
