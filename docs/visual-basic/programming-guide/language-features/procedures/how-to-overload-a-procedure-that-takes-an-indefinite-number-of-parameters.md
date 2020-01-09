---
title: 'Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme'
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
ms.openlocfilehash: 94f12b4cc6cb35864fefbb3b5bb1378bec5e974c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347563"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="8ddf2-102">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ddf2-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="8ddf2-103">Bir yordamın [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi varsa, parametre dizisi için tek boyutlu bir dizi alan aşırı yüklenmiş bir sürüm tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="8ddf2-104">Daha fazla bilgi için, [yordamları aşırı yükleme konusunda dikkat edilmesi gereken](./considerations-in-overloading-procedures.md)"ParamArray parametresi Için örtük aşırı yüklemeler" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="8ddf2-105">Değişken sayıda parametre alan bir yordamı aşırı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="8ddf2-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="8ddf2-106">Bu yordamın ve kod mantığının aşırı yüklenmiş sürümlerden `ParamArray` bir parametreden daha fazla avantaj sağladığı yokunular.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="8ddf2-107">"Aşırı yüklemeler ve ParamArrays" konusuna bakın ve daha fazla [yordamda göz](./considerations-in-overloading-procedures.md)atın.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="8ddf2-108">Yordamın parametre listesinin değişken bölümünde kabul etmesi gereken değer sayısını belirleme.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="8ddf2-109">Bu durum, hiçbir değer olmaması durumunda olabilir ve tek boyutlu bir dizinin durumunu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="8ddf2-110">Her kabul edilebilir sayıda sağlanan değer için, karşılık gelen parametre listesini tanımlayan bir `Sub` veya `Function` bildirim bildirimi yazın.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="8ddf2-111">Bu aşırı yüklenmiş sürümde `Optional` ya da `ParamArray` anahtar sözcüğünü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="8ddf2-112">Her bildirimde, `Sub` veya `Function` anahtar sözcüğünün önüne [aşırı yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="8ddf2-113">Her bildirime göre, çağıran kod bu bildirimin parametre listesine karşılık gelen değerleri sağladığı zaman yürütülmesi gereken yordam kodunu yazın.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="8ddf2-114">Her yordamı uygun şekilde `End Sub` veya `End Function` ifadesiyle sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ddf2-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ddf2-115">Example</span></span>  
 <span data-ttu-id="8ddf2-116">Aşağıdaki örnek, bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresiyle tanımlanan bir yordamı ve daha sonra eşdeğer bir yordam kümesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="8ddf2-117">Parametre dizisi için tek boyutlu bir dizi alan bir parametre listesiyle bu tür bir yordamı aşırı yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="8ddf2-118">Ancak, diğer örtük aşırı yüklemelerin imzalarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="8ddf2-119">Aşağıdaki bildirimlerde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="8ddf2-120">Aşırı yüklenmiş sürümlerindeki kodun, çağıran kodun `ParamArray` parametresi için bir veya daha fazla değer sağlayıp sağlamamasını veya bu durumda kaç tane olacağını test etmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="8ddf2-121">Visual Basic, denetimi çağıran bağımsız değişken listesiyle eşleşen sürüme geçirir.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="8ddf2-122">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="8ddf2-122">Compile the code</span></span>  
 <span data-ttu-id="8ddf2-123">`ParamArray` parametresine sahip bir yordam aşırı yüklenmiş sürümlerin bir kümesiyle eşdeğer olduğundan, böyle bir yordamı bu örtük aşırı yüklemelerin herhangi birine karşılık gelen bir parametre listesiyle birlikte yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="8ddf2-124">Daha fazla bilgi için bkz. [yordamları aşırı yükleme konuları](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8ddf2-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8ddf2-125">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8ddf2-125">.NET Framework Security</span></span>  
 <span data-ttu-id="8ddf2-126">Süresiz olarak büyük olabilecek bir dizi ile uğraşmanız durumunda, uygulamanızın bazı iç kapasitesini çok fazla çalıştırmaya yönelik bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="8ddf2-127">Bir parametre dizisini kabul ediyorsanız, kendisine geçilen çağıran kodun dizinin uzunluğunu test etmeli ve uygulamanız için çok büyükse uygun adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddf2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ddf2-128">See also</span></span>

- [<span data-ttu-id="8ddf2-129">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8ddf2-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8ddf2-130">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8ddf2-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8ddf2-131">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ddf2-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="8ddf2-132">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="8ddf2-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="8ddf2-133">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="8ddf2-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="8ddf2-134">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="8ddf2-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="8ddf2-135">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="8ddf2-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="8ddf2-136">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="8ddf2-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="8ddf2-137">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="8ddf2-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="8ddf2-138">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="8ddf2-138">Overload Resolution</span></span>](./overload-resolution.md)
