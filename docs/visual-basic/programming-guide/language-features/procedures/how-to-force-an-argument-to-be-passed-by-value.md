---
title: 'Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 047738a2cbadc6b7d72f41aade22bbeff16d1bac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347608"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="9c02c-102">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c02c-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="9c02c-103">Yordam bildirimi, geçen mekanizmayı belirler.</span><span class="sxs-lookup"><span data-stu-id="9c02c-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="9c02c-104">Bir parametre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)olarak bildirilirse, Visual Basic karşılık gelen bağımsız değişkeni başvuruya göre geçmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="9c02c-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="9c02c-105">Bu yordam, çağıran koddaki bağımsız değişkenin temelindeki programlama öğesinin değerini değiştirmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="9c02c-106">Temel öğeyi bu değişikliğe karşı korumak istiyorsanız, bağımsız değişken adını parantez içine alarak yordam çağrısındaki `ByRef` geçen mekanizmayı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="9c02c-107">Bu parantezler, çağrısındaki bağımsız değişken listesini çevreleyen parantezler için de ek olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="9c02c-108">Çağıran kod bir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mekanizmasını geçersiz kılamaz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="9c02c-109">Bir bağımsız değişkenin değere göre geçirilmesini zorlamak için</span><span class="sxs-lookup"><span data-stu-id="9c02c-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="9c02c-110">Yordamda karşılık gelen parametre `ByVal` bildirilirse, ek adımlar uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9c02c-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="9c02c-111">Visual Basic, zaten bağımsız değişkeni değere göre geçmesini bekliyor.</span><span class="sxs-lookup"><span data-stu-id="9c02c-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="9c02c-112">Yordamda karşılık gelen parametre `ByRef` bildirilirse, yordam çağrısında bağımsız değişkeni parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="9c02c-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c02c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c02c-113">Example</span></span>  
 <span data-ttu-id="9c02c-114">Aşağıdaki örnek bir `ByRef` parametresi bildirimini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9c02c-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="9c02c-115">`ByVal`zorlayan çağrıda, iki parantez düzeyini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9c02c-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="9c02c-116">`str`, bağımsız değişken listesi içinde fazladan parantez içine alınmışsa, `setNewString` yordamı çağıran koddaki değerini değiştiremez ve "bir ByVal geçirildiğinde değiştirilemez" `MsgBox` görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="9c02c-117">`str` ek parantezler içine alınmadığından, yordamı değiştirebilir `MsgBox` ve "ınString bağımsız değişkeni için yeni bir değer" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="9c02c-118">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="9c02c-118">Compile the code</span></span>  
 <span data-ttu-id="9c02c-119">Bir değişkeni başvuruya göre geçirdiğinizde, bu mekanizmayı belirtmek için `ByRef` anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="9c02c-120">Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="9c02c-121">Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="9c02c-122">Bu, kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9c02c-123">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="9c02c-123">Robust Programming</span></span>  
 <span data-ttu-id="9c02c-124">Bir yordam [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)parametresini bildiriyorsa, kodun doğru yürütülmesi, çağıran kodda temel alınan öğeyi değiştirebilmeyle ilgili olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="9c02c-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="9c02c-125">Çağıran kod, bağımsız değişkeni parantez içine alarak bu çağıran mekanizmayı geçersiz kılıyorsa veya değiştirilemeyen bir bağımsız değişken geçirirse yordam, temel alınan öğeyi değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="9c02c-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="9c02c-126">Bu, çağıran kodda beklenmeyen sonuçlara neden olabilirler.</span><span class="sxs-lookup"><span data-stu-id="9c02c-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9c02c-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9c02c-127">.NET Framework Security</span></span>  
 <span data-ttu-id="9c02c-128">Bir yordamın, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin vermek için her zaman potansiyel bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="9c02c-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="9c02c-129">Bu değerin değiştirilmesini beklediğinizden ve kullanılmadan önce geçerliliği göz önünde denetlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9c02c-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c02c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c02c-130">See also</span></span>

- [<span data-ttu-id="9c02c-131">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9c02c-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9c02c-132">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9c02c-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9c02c-133">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="9c02c-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="9c02c-134">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9c02c-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="9c02c-135">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="9c02c-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="9c02c-136">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="9c02c-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="9c02c-137">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9c02c-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="9c02c-138">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="9c02c-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="9c02c-139">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9c02c-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="9c02c-140">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="9c02c-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
