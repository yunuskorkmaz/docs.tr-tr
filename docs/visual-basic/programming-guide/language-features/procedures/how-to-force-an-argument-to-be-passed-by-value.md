---
title: "Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fdb2df7e114f49c23db9f5b322ca9dd32135ac88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="2ab97-102">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ab97-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="2ab97-103">Yordam bildirimi geçirme mekanizması belirler.</span><span class="sxs-lookup"><span data-stu-id="2ab97-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="2ab97-104">Bir parametre bildirilirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] başvuru ile ilgili bağımsız değişken geçirmek bekliyor.</span><span class="sxs-lookup"><span data-stu-id="2ab97-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="2ab97-105">Bu, çağrıyı yapan kod değişkeninde temel programlama öğenin değerini değiştirmek için yordamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ab97-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="2ab97-106">Temel alınan öğe bu tür değişiklik karşı korumak isterseniz, geçersiz kılabilirsiniz `ByRef` geçirme mekanizması yordamda çağrı parantez içinde bağımsız değişken adı kapsayan tarafından.</span><span class="sxs-lookup"><span data-stu-id="2ab97-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="2ab97-107">Bağımsız değişken listesi çağrısında kapsayan parantez yanı sıra bu parantezler var.</span><span class="sxs-lookup"><span data-stu-id="2ab97-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="2ab97-108">Çağrıyı yapan kod geçersiz kılınamaz bir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mekanizması.</span><span class="sxs-lookup"><span data-stu-id="2ab97-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="2ab97-109">Bağımsız değişkeni değere göre geçirilecek şekilde zorlama</span><span class="sxs-lookup"><span data-stu-id="2ab97-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="2ab97-110">Karşılık gelen bir parametre bildirilirse `ByVal` yordamda herhangi bir ek adımlar gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2ab97-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="2ab97-111">bağımsız değişkeni değere göre geçirilecek zaten bekliyor.</span><span class="sxs-lookup"><span data-stu-id="2ab97-111"> already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="2ab97-112">Karşılık gelen bir parametre bildirilirse `ByRef` bağımsız değişkeni parantez içinde yordam çağrısı yordamda alın.</span><span class="sxs-lookup"><span data-stu-id="2ab97-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ab97-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ab97-113">Example</span></span>  
 <span data-ttu-id="2ab97-114">Aşağıdaki örnekte geçersiz kılan bir `ByRef` parametre bildirimi.</span><span class="sxs-lookup"><span data-stu-id="2ab97-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="2ab97-115">Zorlar çağrısında `ByVal`, parantez iki düzeyde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2ab97-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 <span data-ttu-id="2ab97-116">Zaman `str` bağımsız değişken listesi içinde ek parantez içine `setNewString` yordamı çağıran kodu değerini değiştiremez ve `MsgBox` "değiştirilemez, ByVal aktarılırsa" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ab97-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="2ab97-117">Zaman `str` içine alınmayan fazladan parantez içinde yordamı, değiştirebilir ve `MsgBox` "Bu inString bağımsız değişken için yeni bir değer" görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="2ab97-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ab97-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2ab97-118">Compiling the Code</span></span>  
 <span data-ttu-id="2ab97-119">Başvuruya göre bir değişken geçirdiğinizde kullanmalısınız `ByRef` anahtar Bu mekanizma belirtin.</span><span class="sxs-lookup"><span data-stu-id="2ab97-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="2ab97-120">Varsayılan olarak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bağımsız değişkenleri değere göre geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="2ab97-120">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="2ab97-121">Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="2ab97-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="2ab97-122">Bu, kodunuzu okumak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2ab97-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2ab97-123">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2ab97-123">Robust Programming</span></span>  
 <span data-ttu-id="2ab97-124">Bir yordam bir parametre bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), doğru kodunun yürütülmesini çağıran kodu temel alınan öğe değiştirme yetkisi olan bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ab97-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="2ab97-125">Çağrıyı yapan kod parantez içinde bağımsız değişken kapsayan tarafından bu arama mekanizması kılıyorsa veya değiştirilemez bağımsız değişkeni geçerse yordamı temel öğesi değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ab97-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="2ab97-126">Bu, çağrıyı yapan kod beklenmeyen sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="2ab97-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2ab97-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="2ab97-127">.NET Framework Security</span></span>  
 <span data-ttu-id="2ab97-128">Yoktur her zaman potansiyel bir risk çağıran kodu bir bağımsız değişken alttaki değerini değiştirmek bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ab97-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="2ab97-129">Bu değeri değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="2ab97-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab97-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab97-130">See Also</span></span>  
 [<span data-ttu-id="2ab97-131">Yordamları</span><span class="sxs-lookup"><span data-stu-id="2ab97-131">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="2ab97-132">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2ab97-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="2ab97-133">Nasıl yapılır: bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="2ab97-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="2ab97-134">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="2ab97-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="2ab97-135">Değiştirilebilir ve değiştirilemez bağımsız değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="2ab97-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="2ab97-136">Değere ve başvuruya göre bağımsız değişken geçirme arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="2ab97-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="2ab97-137">Nasıl yapılır: bir yordam bağımsız değişkeninin değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="2ab97-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="2ab97-138">Nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma</span><span class="sxs-lookup"><span data-stu-id="2ab97-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="2ab97-139">Bağımsız değişkenleri konuma göre ve ada göre geçirme</span><span class="sxs-lookup"><span data-stu-id="2ab97-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="2ab97-140">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="2ab97-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
