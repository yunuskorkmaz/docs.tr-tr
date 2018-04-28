---
title: 'Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cb4faa2dfd01f854dcc3bf8c2a330adf5acdcac
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="67e2e-102">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67e2e-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="67e2e-103">Bir yordam varsa bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi, tek boyutlu bir dizi parametre dizisi için ayırdığınız aşırı yüklenmiş bir sürümünü tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="67e2e-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="67e2e-104">Daha fazla bilgi için bkz: "Örtük aşırı yüklemeler için bir ParamArray parametre" [aşırı yükleme yordamları konuları](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="67e2e-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="67e2e-105">Değişken sayıda parametre isteyen bir yordamı aşırı yükleme için</span><span class="sxs-lookup"><span data-stu-id="67e2e-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="67e2e-106">Yordam ve kod mantığı avantajları gelen çağırma sürümlerden birden fazla aşırı onaylaması bir `ParamArray` parametresi.</span><span class="sxs-lookup"><span data-stu-id="67e2e-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="67e2e-107">"Aşırı ve ParamArrays" bölümüne bakın [yordamları aşırı yüklemeye ilişkin düşünceler](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="67e2e-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="67e2e-108">Sağlanan değerlerin hangi numaraları yordamı parametre listesi değişken bölümünde kabul etmelidir saptayın.</span><span class="sxs-lookup"><span data-stu-id="67e2e-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="67e2e-109">Bu değer durumunun içerebilir ve tek tek boyutlu dizi durumunun içerebilir.</span><span class="sxs-lookup"><span data-stu-id="67e2e-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="67e2e-110">Sağlanan değerleri kabul edilebilir her sayısı için yazma bir `Sub` veya `Function` karşılık gelen parametre listesi tanımlar bildirimi deyimi.</span><span class="sxs-lookup"><span data-stu-id="67e2e-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="67e2e-111">Ya da kullanmayın `Optional` veya `ParamArray` Bu aşırı yüklenmiş sürümünde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="67e2e-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="67e2e-112">Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğüyle [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="67e2e-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="67e2e-113">Her bildirim bildirim ait parametre listesine karşılık gelen değer çağıran kodu sağlıyor yükleyen yürütülecek yordamı kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="67e2e-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="67e2e-114">Her bir yordam ile sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="67e2e-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67e2e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="67e2e-115">Example</span></span>  
 <span data-ttu-id="67e2e-116">İle tanımlanmış bir yordam aşağıdaki örnekte bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametre ve eşdeğer bir aşırı yüklenmiş yordamlar dizisi.</span><span class="sxs-lookup"><span data-stu-id="67e2e-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 <span data-ttu-id="67e2e-117">Tek boyutlu bir dizi parametre dizisi için gereken bir parametre listesi ile bu tür bir yordamı aşırı yükleme yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="67e2e-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="67e2e-118">Ancak, diğer örtük aşırı imzalarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e2e-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="67e2e-119">Aşağıdaki bildirimler bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67e2e-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 <span data-ttu-id="67e2e-120">Çağrıyı yapan kod için bir veya daha fazla değer sağlanan olup olmadığını sınamak aşırı yüklü sürümlerini koddaki yok `ParamArray` parametresi veya ise, kaç tane.</span><span class="sxs-lookup"><span data-stu-id="67e2e-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="67e2e-121">Visual Basic çağırma bağımsız değişken listesi eşleşen sürüm denetimi geçirir.</span><span class="sxs-lookup"><span data-stu-id="67e2e-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="67e2e-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="67e2e-122">Compiling the Code</span></span>  
 <span data-ttu-id="67e2e-123">Çünkü bir yordama bir `ParamArray` parametre kümesi aşırı yüklenmiş sürümleri için eşdeğer ve bu örtük aşırı yüklemeleri birine karşılık gelen bir parametre listesi ile bu tür bir yordamı tekrar yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="67e2e-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="67e2e-124">Daha fazla bilgi için bkz: [aşırı yükleme yordamları konuları](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="67e2e-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="67e2e-125">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67e2e-125">.NET Framework Security</span></span>  
 <span data-ttu-id="67e2e-126">Süresiz olarak büyük olabilen bir dizi ile ilgilenir olduğunda, uygulamanızın iç bazı kapasite taşmasını riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="67e2e-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="67e2e-127">Bir parametre dizisi kabul ederseniz, çağrıyı yapan kod kendisine geçirilen dizi uzunluğu, test ve uygulamanız için çok büyük ise uygun adımları gerçekleştirin gerekir.</span><span class="sxs-lookup"><span data-stu-id="67e2e-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e2e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67e2e-128">See Also</span></span>  
 [<span data-ttu-id="67e2e-129">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="67e2e-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="67e2e-130">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="67e2e-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="67e2e-131">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="67e2e-131">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="67e2e-132">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="67e2e-132">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="67e2e-133">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="67e2e-133">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="67e2e-134">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="67e2e-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="67e2e-135">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="67e2e-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="67e2e-136">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="67e2e-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="67e2e-137">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="67e2e-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="67e2e-138">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="67e2e-138">Overload Resolution</span></span>](./overload-resolution.md)
