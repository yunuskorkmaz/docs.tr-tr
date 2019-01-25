---
title: 'Nasıl yapılır: (Visual Basic) isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme'
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
ms.openlocfilehash: 343ede485a0486567710a8bf34d85ea356c139fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694132"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="6e6d5-102">Nasıl yapılır: (Visual Basic) isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="6e6d5-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="6e6d5-103">Bir veya daha fazla yordam varsa, [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametreleri, herhangi bir örtük bunun aşırı yüklerinden eşleşen aşırı yüklenmiş bir sürümünü tanımlayamaz.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="6e6d5-104">"Daha fazla bilgi için örtük aşırı yüklemeleri için isteğe bağlı parametreleri" bölümüne bakın [aşırı yükleme yordamları Hususlarına](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6e6d5-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="6e6d5-105">Bir isteğe bağlı parametre</span><span class="sxs-lookup"><span data-stu-id="6e6d5-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="6e6d5-106">İsteğe bağlı bir parametre isteyen bir yordamı aşırı yükleme için</span><span class="sxs-lookup"><span data-stu-id="6e6d5-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="6e6d5-107">Yazma bir `Sub` veya `Function` parametre listesinde isteğe bağlı parametre içeren bildirim deyimindeki.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="6e6d5-108">Kullanmayın `Optional` anahtar sözcüğü Bu aşırı yüklenmiş bir sürüm.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="6e6d5-109">Önünde `Sub` veya `Function` anahtar sözcüğü ile [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="6e6d5-110">Çağıran kod sağlayan isteğe bağlı bağımsız değişken olduğunda yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="6e6d5-111">Yordama sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="6e6d5-112">İsteğe bağlı parametresi parametre listesinde içermez dışında ilk bildirimi için aynı olan ikinci bir bildirim deyiminin yazın.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="6e6d5-113">Çağıran kod, isteğe bağlı bağımsız değişken sağlamıyor yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="6e6d5-114">Yordama sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="6e6d5-115">Aşağıdaki örnek, iki aşırı yüklenmiş yordamlar ve son olarak geçersiz ve geçerli aşırı yüklü sürümlerini örnekleri bir denk kümesi bir isteğe bağlı parametresi tanımlı bir yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="6e6d5-116">Birden fazla isteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="6e6d5-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="6e6d5-117">Birden fazla isteğe bağlı parametre içeren bir yordam için normalde ikiden fazla aşırı yüklenmiş sürümleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="6e6d5-118">Örneğin, iki isteğe bağlı parametre vardır ve çağıran kod sağlayın veya her biri birbirinden atlarsanız, belirtilen bağımsız değişkenleri her bir olası kombinasyonu için dört aşırı yüklenmiş sürümleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="6e6d5-119">İsteğe bağlı parametrelerin sayısı arttıkça, aşırı yükleme karmaşıklığı artırır.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="6e6d5-120">N isteğe bağlı parametreler için sağlanan bağımsız değişkenler bazı birleşimlerini kabul edilebilir olmayan sürece 2 gereksinim ^ N aşırı yüklü sürümler.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="6e6d5-121">Yordamı doğasına bağlı olarak, mantıksal netliğini tüm aşırı yüklenmiş sürümleri tanımlama için fazladan çaba yaslar bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="6e6d5-122">Birden fazla isteğe bağlı parametre isteyen bir yordamı aşırı yükleme için</span><span class="sxs-lookup"><span data-stu-id="6e6d5-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="6e6d5-123">Sağlanan isteğe bağlı bağımsız değişkenlere hangi birleşimleri yordamın mantığı için kabul edilebilir olduğunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="6e6d5-124">İsteğe bağlı bir parametre başka bağlıysa kabul edilemez bir birleşimi ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="6e6d5-125">Örneğin, bir parametre bir eşin adını kabul eder ve başka bir eşin yaş kabul eder, yaş sağlama ancak ad atlama bağımsız değişkenlerin bir birleşimi kabul edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="6e6d5-126">Sağlanan isteğe bağlı bağımsız değişkenler için her kabul edilebilir birleşim yazma bir `Sub` veya `Function` bildirim deyimindeki, karşılık gelen parametre listesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="6e6d5-127">Kullanmayın `Optional` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="6e6d5-128">Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğü ile [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="6e6d5-129">Her bildirimi çağıran kod sağlayan bu bildirimin parametre listesine karşılık gelen bir bağımsız değişken listesi, yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="6e6d5-130">Her bir yordam sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6d5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e6d5-131">See also</span></span>
- [<span data-ttu-id="6e6d5-132">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="6e6d5-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6e6d5-133">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="6e6d5-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6e6d5-134">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e6d5-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="6e6d5-135">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="6e6d5-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="6e6d5-136">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="6e6d5-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="6e6d5-137">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="6e6d5-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="6e6d5-138">Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="6e6d5-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="6e6d5-139">Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="6e6d5-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="6e6d5-140">Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="6e6d5-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="6e6d5-141">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="6e6d5-141">Overload Resolution</span></span>](./overload-resolution.md)
