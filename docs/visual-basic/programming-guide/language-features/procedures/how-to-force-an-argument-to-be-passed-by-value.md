---
title: 'Nasıl yapılır: Bağımsız değişkeni (Visual Basic) değere göre geçirilecek şekilde zorlama'
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
ms.openlocfilehash: 497ae11b858b7d164ba3b5607ff2109254a154de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863629"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="8da03-102">Nasıl yapılır: Bağımsız değişkeni (Visual Basic) değere göre geçirilecek şekilde zorlama</span><span class="sxs-lookup"><span data-stu-id="8da03-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="8da03-103">Yordam bildirimi geçirme mekanizması belirler.</span><span class="sxs-lookup"><span data-stu-id="8da03-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="8da03-104">Bir parametre bildirilirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic bekliyor karşılık gelen bağımsız değişken başvuru ile geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="8da03-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="8da03-105">Bu yordam çağıran koddaki bağımsız değişken temel programlama öğenin değerini değiştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8da03-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="8da03-106">Temel alınan öğe bu tür değişiklik karşı korumak istiyorsanız, geçersiz kılabilirsiniz `ByRef` geçirme mekanizmasında yordamı çağırma bağımsız değişken adı parantez içine alarak.</span><span class="sxs-lookup"><span data-stu-id="8da03-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="8da03-107">Çağrısında bağımsız değişken listesini çevreleyen parantezler yanı sıra bu parantezler var.</span><span class="sxs-lookup"><span data-stu-id="8da03-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="8da03-108">Çağıran kod geçersiz kılamaz bir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mekanizması.</span><span class="sxs-lookup"><span data-stu-id="8da03-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="8da03-109">Bağımsız değişkeni değere göre geçirilecek şekilde zorlama</span><span class="sxs-lookup"><span data-stu-id="8da03-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="8da03-110">Karşılık gelen parametre bildirilirse `ByVal` yordamda herhangi bir ek adımlar gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8da03-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="8da03-111">Visual Basic bağımsız değişkeni değere göre geçirilecek zaten bekliyor.</span><span class="sxs-lookup"><span data-stu-id="8da03-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="8da03-112">Karşılık gelen parametre bildirilirse `ByRef` parantez yordam çağrısı içinde bağımsız değişkeni yordamda alın.</span><span class="sxs-lookup"><span data-stu-id="8da03-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8da03-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8da03-113">Example</span></span>  
 <span data-ttu-id="8da03-114">Aşağıdaki örnek geçersiz kılan bir `ByRef` parametre bildirimi.</span><span class="sxs-lookup"><span data-stu-id="8da03-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="8da03-115">Zorlayan çağrısında `ByVal`, iki düzeyi parantez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8da03-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="8da03-116">Zaman `str` bağımsız değişken listesi içinde ek parantez içine `setNewString` yordamı çağıran koddaki değerini değiştiremez ve `MsgBox` "değiştirilemez, ByVal aktarılırsa" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8da03-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="8da03-117">Zaman `str` içine alınmayan ek parantez içine yordamı, değiştirebilir ve `MsgBox` görüntüler "İnString bağımsız değişken için yeni bir değer budur."</span><span class="sxs-lookup"><span data-stu-id="8da03-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8da03-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8da03-118">Compiling the Code</span></span>  
 <span data-ttu-id="8da03-119">Başvuruya göre değişken başarıyla sonuçlandıktan sonra kullanmalısınız `ByRef` Bu mekanizma belirtmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8da03-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="8da03-120">Visual Basic'te bağımsız değişkenleri değere göre geçirilecek varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="8da03-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="8da03-121">Ancak, iyi bir ya da içerecek şekilde programlama [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğü ile bildirilen her parametre.</span><span class="sxs-lookup"><span data-stu-id="8da03-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="8da03-122">Bu, kodunuzu daha kolay okunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8da03-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8da03-123">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8da03-123">Robust Programming</span></span>  
 <span data-ttu-id="8da03-124">Bir yordam parametre bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kodun doğru yürütme çağıran koddaki temel alınan öğeyi değiştirmek için bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8da03-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="8da03-125">Çağıran kod, bağımsız değişken parantez içine alarak çağıran Bu mekanizma geçersiz kılar veya değiştirilemez bir bağımsız değişken geçerse, temel alınan öğe yordamı değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8da03-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="8da03-126">Bu, çağıran koddaki beklenmeyen sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="8da03-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8da03-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8da03-127">.NET Framework Security</span></span>  
 <span data-ttu-id="8da03-128">Her zaman bir olası riski yoktur çağıran koddaki bağımsız değişken temel değeri değiştirmek bir yordam vermek.</span><span class="sxs-lookup"><span data-stu-id="8da03-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="8da03-129">Bu değer, değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="8da03-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da03-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8da03-130">See also</span></span>

- [<span data-ttu-id="8da03-131">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8da03-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8da03-132">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="8da03-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8da03-133">Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="8da03-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="8da03-134">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="8da03-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="8da03-135">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="8da03-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="8da03-136">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="8da03-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="8da03-137">Nasıl yapılır: Bir yordam bağımsız değişkeninin değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="8da03-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="8da03-138">Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma</span><span class="sxs-lookup"><span data-stu-id="8da03-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="8da03-139">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="8da03-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="8da03-140">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="8da03-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
