---
title: 'Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 1da1d67726a9669477721aabc0aace0119aa7e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652902"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="c1cae-102">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1cae-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="c1cae-103">Bir veya daha fazla yordam varsa, [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametreleri örtük aşırı hiçbiriyle aşırı yüklenmiş bir sürümünü tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c1cae-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="c1cae-104">"Daha fazla bilgi için örtük aşırı yüklemeler için isteğe bağlı parametreleri" bölümüne bakın [aşırı yükleme yordamları konuları](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c1cae-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="c1cae-105">İsteğe bağlı bir parametre</span><span class="sxs-lookup"><span data-stu-id="c1cae-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="c1cae-106">İsteğe bağlı bir parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="c1cae-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="c1cae-107">Yazma bir `Sub` veya `Function` parametre listesinde isteğe bağlı bir parametre içeren bildirimi deyimi.</span><span class="sxs-lookup"><span data-stu-id="c1cae-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="c1cae-108">Kullanmayın `Optional` Bu aşırı yüklenmiş sürümünde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c1cae-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="c1cae-109">Öncesinde `Sub` veya `Function` anahtar sözcüğüyle [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c1cae-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="c1cae-110">İsteğe bağlı bağımsız değişkeni çağıran kodu sağlar, yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="c1cae-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="c1cae-111">Yordamını sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="c1cae-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="c1cae-112">İsteğe bağlı parametre parametre listesinde içermez ancak bu, ilk bildirimine aynı ikinci bir bildirim deyimi yazma.</span><span class="sxs-lookup"><span data-stu-id="c1cae-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="c1cae-113">Çağrıyı yapan kod isteğe bağlı bağımsız değişkeni sağlamaz, yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="c1cae-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="c1cae-114">Yordamını sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="c1cae-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="c1cae-115">Aşağıdaki örnekte iki aşırı yüklenmiş yordamlar ve son olarak geçersiz ve geçerli aşırı yüklenmiş sürümlerinin örnekleri eşdeğer bir dizi bir isteğe bağlı parametresi tanımlı bir yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1cae-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="c1cae-116">Birden çok isteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="c1cae-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="c1cae-117">Birden fazla isteğe bağlı bir parametre ile bir yordam için normalde ikiden fazla aşırı yüklenmiş sürümlerin gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1cae-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="c1cae-118">Örneğin, iki isteğe bağlı parametreler vardır ve çağıran kodu sağlayın veya diğer bağımsız olarak her biri atlarsanız, dört aşırı yüklenmiş sürümlerin sağlanan bağımsız değişkenler her bir olası kombinasyonu için bir tane gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1cae-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="c1cae-119">İsteğe bağlı parametrelerin sayısı arttıkça, aşırı yüklemesi karmaşıklığını artırır.</span><span class="sxs-lookup"><span data-stu-id="c1cae-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="c1cae-120">N isteğe bağlı parametreler için bazı birleşimleri sağlanan bağımsız değişkenler için kabul edilebilir değil sürece 2 gereksinim ^ N aşırı sürümleri.</span><span class="sxs-lookup"><span data-stu-id="c1cae-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="c1cae-121">Yordam yapısına bağlı mantığı netlik aşırı yüklenmiş tüm sürümleri tanımlamanın ek çaba hizalar bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1cae-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="c1cae-122">Birden fazla isteğe bağlı bir parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="c1cae-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="c1cae-123">Hangi sağlanan isteğe bağlı bağımsız değişkenler yordamı mantığı için kabul edilebilir birleşimleridir belirler.</span><span class="sxs-lookup"><span data-stu-id="c1cae-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="c1cae-124">İsteğe bağlı bir parametre başka bağımlıysa kabul edilebilir bir birleşimi ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="c1cae-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="c1cae-125">Örneğin, bir parametre bir eşin adını kabul eder ve başka eşinin yaş kabul eder, yaş sağladığını ancak adı atlama bağımsız değişkenler bileşimi kabul edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="c1cae-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="c1cae-126">Sağlanan isteğe bağlı bağımsız değişkenler kabul edilebilir her birleşimi için yazma bir `Sub` veya `Function` karşılık gelen parametre listesi tanımlar bildirimi deyimi.</span><span class="sxs-lookup"><span data-stu-id="c1cae-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="c1cae-127">Kullanmayın `Optional` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c1cae-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="c1cae-128">Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğüyle [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c1cae-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="c1cae-129">Her bildirim çağrıyı yapan kod bildirim ait parametre listesine karşılık gelen bir bağımsız değişken listesi sağlar, yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="c1cae-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="c1cae-130">Her bir yordam ile sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="c1cae-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1cae-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1cae-131">See Also</span></span>  
 [<span data-ttu-id="c1cae-132">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c1cae-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="c1cae-133">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="c1cae-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c1cae-134">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1cae-134">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="c1cae-135">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="c1cae-135">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="c1cae-136">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="c1cae-136">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="c1cae-137">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="c1cae-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="c1cae-138">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="c1cae-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="c1cae-139">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="c1cae-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="c1cae-140">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="c1cae-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="c1cae-141">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="c1cae-141">Overload Resolution</span></span>](./overload-resolution.md)
