---
title: 'Nasıl yapılır: Bir belirsiz sayıda parametre (Visual Basic) isteyen bir yordamı aşırı yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 3cf75fc6221364704379eb23d308481c34e6c0d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955747"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="48e9e-102">Nasıl yapılır: Bir belirsiz sayıda parametre (Visual Basic) isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="48e9e-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="48e9e-103">Bir yordam varsa bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi, parametre dizisi için tek boyutlu bir dizi alan aşırı yüklenmiş bir sürümünü tanımlayamaz.</span><span class="sxs-lookup"><span data-stu-id="48e9e-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="48e9e-104">Daha fazla bilgi için bkz: "Örtük aşırı yüklemeleri için bir ParamArray parametresiyle" [aşırı yükleme yordamları Hususlarına](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="48e9e-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="48e9e-105">Değişken sayıda parametre isteyen bir yordamı aşırı yükleme için</span><span class="sxs-lookup"><span data-stu-id="48e9e-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="48e9e-106">Yordam ve kod mantıksal avantajlarından çağırma sürümlerinden birden fazla aşırı anlamamıza bir `ParamArray` parametresi.</span><span class="sxs-lookup"><span data-stu-id="48e9e-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="48e9e-107">"Aşırı yüklemeler ve ParamArrays" konularına bakın [yordamları aşırı yüklemeye ilişkin düşünceler](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="48e9e-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="48e9e-108">Sağlanan değerler hangi sayıda yordam parametre listesi değişken parçası kabul etmelidir belirleyin.</span><span class="sxs-lookup"><span data-stu-id="48e9e-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="48e9e-109">Bu değer harf içerebilir ve tek tek boyutlu bir dizi harf içerebilir.</span><span class="sxs-lookup"><span data-stu-id="48e9e-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="48e9e-110">Sağlanan değerler kabul edilebilir her sayısı için yazma bir `Sub` veya `Function` bildirim deyimindeki, karşılık gelen parametre listesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48e9e-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="48e9e-111">Ya da kullanmayın `Optional` veya `ParamArray` anahtar sözcüğü Bu aşırı yüklenmiş bir sürüm.</span><span class="sxs-lookup"><span data-stu-id="48e9e-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="48e9e-112">Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğü ile [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="48e9e-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="48e9e-113">Her bildirimi çağıran kod, bildirimin parametre listesine karşılık gelen değerlerini sağlayan, yürütülecek yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="48e9e-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="48e9e-114">Her bir yordam sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="48e9e-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48e9e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="48e9e-115">Example</span></span>  
 <span data-ttu-id="48e9e-116">Aşağıdaki örnek, tanımlı bir yordam gösterir. bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi ve aşırı yüklenmiş yordamları eşdeğer bir dizi.</span><span class="sxs-lookup"><span data-stu-id="48e9e-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="48e9e-117">Böyle bir yordam bir parametre listesiyle parametre dizisi için tek boyutlu bir dizi alan aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="48e9e-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="48e9e-118">Ancak, bir örtük aşırı imzalarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48e9e-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="48e9e-119">Aşağıdaki bildirimleri bu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="48e9e-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="48e9e-120">Çağıran kod tarafından sağlanan bir veya daha fazla değer için olup olmadığını sınamak aşırı yüklenmiş sürümleri kodda yok `ParamArray` parametresi veya ise, kaç tane.</span><span class="sxs-lookup"><span data-stu-id="48e9e-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="48e9e-121">Visual Basic denetim çağırma bağımsız değişken listesiyle eşleşen sürüme geçer.</span><span class="sxs-lookup"><span data-stu-id="48e9e-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48e9e-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="48e9e-122">Compiling the Code</span></span>  
 <span data-ttu-id="48e9e-123">Çünkü bir yordama bir `ParamArray` parametre kümesi aşırı yüklü sürümler için eşdeğerdir, örtük Bu aşırı yüklemeler birine karşılık gelen bir parametre listesi ile bu tür bir yordamı aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="48e9e-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="48e9e-124">Daha fazla bilgi için [aşırı yükleme yordamları Hususlarına](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="48e9e-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="48e9e-125">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="48e9e-125">.NET Framework Security</span></span>  
 <span data-ttu-id="48e9e-126">Süresiz olarak büyük olabilecek bir dizi işlem olduğunda, uygulamanızın bazı iç kapasite taşmasını riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="48e9e-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="48e9e-127">Bir parametre dizisi kabul ederseniz, çağıran kodun geçirilen dizinin uzunluğunu test etmek ve uygulamanız için çok büyük ise, uygulamanız gereken adımlar gerekir.</span><span class="sxs-lookup"><span data-stu-id="48e9e-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e9e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48e9e-128">See also</span></span>

- [<span data-ttu-id="48e9e-129">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="48e9e-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="48e9e-130">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="48e9e-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="48e9e-131">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="48e9e-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="48e9e-132">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="48e9e-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="48e9e-133">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="48e9e-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="48e9e-134">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="48e9e-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="48e9e-135">Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="48e9e-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="48e9e-136">Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="48e9e-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="48e9e-137">Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="48e9e-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="48e9e-138">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="48e9e-138">Overload Resolution</span></span>](./overload-resolution.md)
