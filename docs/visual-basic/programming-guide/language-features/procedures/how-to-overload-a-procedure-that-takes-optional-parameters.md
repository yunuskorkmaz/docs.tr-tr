---
title: 'Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme'
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
ms.openlocfilehash: 78ca6b2b95dfd5a7f208e5251f08dfccc5514946
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071527"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="bb8f9-102">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb8f9-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>

<span data-ttu-id="bb8f9-103">Bir yordamda bir veya daha fazla [Isteğe bağlı](../../../language-reference/modifiers/optional.md) parametre varsa, örtük aşırı yüklemelerinin hiçbiriyle eşleşen aşırı yüklenmiş bir sürüm tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-103">If a procedure has one or more [Optional](../../../language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="bb8f9-104">Daha fazla bilgi için bkz. Opsiyonel [yükleme yordamlarına göz](./considerations-in-overloading-procedures.md)atın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="bb8f9-105">Bir Isteğe bağlı parametre</span><span class="sxs-lookup"><span data-stu-id="bb8f9-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="bb8f9-106">İsteğe bağlı bir parametre alan bir yordamı aşırı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="bb8f9-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="bb8f9-107">`Sub` `Function` Parametre listesinde isteğe bağlı parametreyi içeren bir veya bildirim bildirimi yazın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="bb8f9-108">`Optional`Bu aşırı yüklenmiş sürümde anahtar sözcüğünü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="bb8f9-109">`Sub` `Function` [Aşırı yüklemeler](../../../language-reference/modifiers/overloads.md) anahtar sözcüğüyle veya anahtar kelimeden önce.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="bb8f9-110">Çağıran kod isteğe bağlı bağımsız değişkeni sağladığı zaman yürütülmesi gereken yordam kodunu yazın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="bb8f9-111">Yordamı `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="bb8f9-112">Parametre listesinde isteğe bağlı parametreyi içermediği hariç birinci bildirimle özdeş ikinci bir bildirim bildirimi yazın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="bb8f9-113">Çağıran kod isteğe bağlı bağımsız değişkeni sağlamadığınızda yürütülmesi gereken yordam kodunu yazın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="bb8f9-114">Yordamı `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="bb8f9-115">Aşağıdaki örnek, isteğe bağlı bir parametre ile tanımlanan, iki aşırı yüklenmiş yordamın eşdeğer bir kümesini ve son olarak hem geçersiz hem de geçerli aşırı yüklenmiş sürümlerin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="bb8f9-116">Birden çok Isteğe bağlı parametre</span><span class="sxs-lookup"><span data-stu-id="bb8f9-116">Multiple Optional Parameters</span></span>  

 <span data-ttu-id="bb8f9-117">Birden fazla isteğe bağlı parametreye sahip bir yordam için normalde ikiden fazla aşırı yüklenmiş sürüm gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="bb8f9-118">Örneğin, isteğe bağlı iki parametre varsa ve çağıran kod, birbirinden bağımsız olarak her birini belirtebilir veya atlayabilir, sağlanan bağımsız değişkenlerin her bir birleşimi için bir tane olmak üzere dört aşırı yüklü sürüme ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="bb8f9-119">İsteğe bağlı parametrelerin sayısı arttıkça aşırı yüklemenin karmaşıklığı artar.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="bb8f9-120">Sağlanan bağımsız değişkenlerin bazı birleşimleri kabul edilemez değilse, N isteğe bağlı parametre için 2 ^ N aşırı yüklenmiş sürüme ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="bb8f9-121">Yordamın doğasına bağlı olarak, tüm aşırı yüklenmiş sürümlerin tanımlanmasıyla ilgili ekstra çabaların açıklık netliği olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="bb8f9-122">Birden fazla isteğe bağlı parametre alan bir yordamı aşırı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="bb8f9-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="bb8f9-123">Sağlanan isteğe bağlı bağımsız değişkenlerin hangi birleşimlerinin yordamın mantığı için kabul edilebilir olduğunu belirleme.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="bb8f9-124">İsteğe bağlı bir parametre diğerine bağımlıysa, kabul edilemez bir bileşim meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="bb8f9-125">Örneğin, bir parametre kişinin adını kabul ediyorsa ve başka birinin yaşını kabul ediyorsa, yaşı sağlayan bağımsız değişkenlerin bir birleşimi ve adı yok edilemez.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="bb8f9-126">Sağlanan isteğe bağlı bağımsız değişkenlerin her bir kabul edilebilir kombinasyonu için `Sub` , `Function` karşılık gelen parametre listesini tanımlayan bir veya bildirim bildirimi yazın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="bb8f9-127">`Optional`Anahtar sözcüğünü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="bb8f9-128">Her bildirimde, `Sub` veya `Function` anahtar sözcüğünün önüne [aşırı yüklemeler](../../../language-reference/modifiers/overloads.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="bb8f9-129">Her bildirime göre, çağıran kod bu bildirimin parametre listesine karşılık gelen bir bağımsız değişken listesi sağladığı zaman yürütülmesi gereken yordam kodunu yazın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="bb8f9-130">Her yordamı `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8f9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb8f9-131">See also</span></span>

- [<span data-ttu-id="bb8f9-132">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="bb8f9-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bb8f9-133">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bb8f9-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bb8f9-134">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb8f9-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="bb8f9-135">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="bb8f9-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="bb8f9-136">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="bb8f9-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="bb8f9-137">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="bb8f9-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="bb8f9-138">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="bb8f9-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="bb8f9-139">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="bb8f9-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="bb8f9-140">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="bb8f9-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="bb8f9-141">Aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="bb8f9-141">Overload Resolution</span></span>](./overload-resolution.md)
