---
title: 'Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 30f5e5fe7b9c92f90673dc99a0e299136a38305b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="edbc9-102">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edbc9-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="edbc9-103">Yordam bildirimi geçirme mekanizması belirler.</span><span class="sxs-lookup"><span data-stu-id="edbc9-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="edbc9-104">Bir parametre bildirilirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic başvuru ile ilgili bağımsız değişken geçirmek bekliyor.</span><span class="sxs-lookup"><span data-stu-id="edbc9-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="edbc9-105">Bu, çağrıyı yapan kod değişkeninde temel programlama öğenin değerini değiştirmek için yordamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="edbc9-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="edbc9-106">Temel alınan öğe bu tür değişiklik karşı korumak isterseniz, geçersiz kılabilirsiniz `ByRef` geçirme mekanizması yordamda çağrı parantez içinde bağımsız değişken adı kapsayan tarafından.</span><span class="sxs-lookup"><span data-stu-id="edbc9-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="edbc9-107">Bağımsız değişken listesi çağrısında kapsayan parantez yanı sıra bu parantezler var.</span><span class="sxs-lookup"><span data-stu-id="edbc9-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="edbc9-108">Çağrıyı yapan kod geçersiz kılınamaz bir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mekanizması.</span><span class="sxs-lookup"><span data-stu-id="edbc9-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="edbc9-109">Bağımsız değişkeni değere göre geçirilecek şekilde zorlama</span><span class="sxs-lookup"><span data-stu-id="edbc9-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="edbc9-110">Karşılık gelen bir parametre bildirilirse `ByVal` yordamda herhangi bir ek adımlar gerekmez.</span><span class="sxs-lookup"><span data-stu-id="edbc9-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="edbc9-111">Visual Basic zaten bağımsız değişkeni değere göre geçirilecek bekliyor.</span><span class="sxs-lookup"><span data-stu-id="edbc9-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="edbc9-112">Karşılık gelen bir parametre bildirilirse `ByRef` bağımsız değişkeni parantez içinde yordam çağrısı yordamda alın.</span><span class="sxs-lookup"><span data-stu-id="edbc9-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edbc9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="edbc9-113">Example</span></span>  
 <span data-ttu-id="edbc9-114">Aşağıdaki örnekte geçersiz kılan bir `ByRef` parametre bildirimi.</span><span class="sxs-lookup"><span data-stu-id="edbc9-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="edbc9-115">Zorlar çağrısında `ByVal`, parantez iki düzeyde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="edbc9-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 <span data-ttu-id="edbc9-116">Zaman `str` bağımsız değişken listesi içinde ek parantez içine `setNewString` yordamı çağıran kodu değerini değiştiremez ve `MsgBox` "değiştirilemez, ByVal aktarılırsa" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="edbc9-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="edbc9-117">Zaman `str` içine alınmayan fazladan parantez içinde yordamı, değiştirebilir ve `MsgBox` "Bu inString bağımsız değişken için yeni bir değer" görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="edbc9-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="edbc9-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="edbc9-118">Compiling the Code</span></span>  
 <span data-ttu-id="edbc9-119">Başvuruya göre bir değişken geçirdiğinizde kullanmalısınız `ByRef` anahtar Bu mekanizma belirtin.</span><span class="sxs-lookup"><span data-stu-id="edbc9-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="edbc9-120">Visual Basic'de bağımsız değişkenleri değere göre geçirilecek varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="edbc9-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="edbc9-121">Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="edbc9-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="edbc9-122">Bu, kodunuzu okumak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="edbc9-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="edbc9-123">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="edbc9-123">Robust Programming</span></span>  
 <span data-ttu-id="edbc9-124">Bir yordam bir parametre bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), doğru kodunun yürütülmesini çağıran kodu temel alınan öğe değiştirme yetkisi olan bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="edbc9-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="edbc9-125">Çağrıyı yapan kod parantez içinde bağımsız değişken kapsayan tarafından bu arama mekanizması kılıyorsa veya değiştirilemez bağımsız değişkeni geçerse yordamı temel öğesi değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="edbc9-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="edbc9-126">Bu, çağrıyı yapan kod beklenmeyen sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="edbc9-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="edbc9-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="edbc9-127">.NET Framework Security</span></span>  
 <span data-ttu-id="edbc9-128">Yoktur her zaman potansiyel bir risk çağıran kodu bir bağımsız değişken alttaki değerini değiştirmek bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="edbc9-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="edbc9-129">Bu değeri değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="edbc9-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbc9-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="edbc9-130">See Also</span></span>  
 [<span data-ttu-id="edbc9-131">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="edbc9-131">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="edbc9-132">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="edbc9-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="edbc9-133">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="edbc9-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="edbc9-134">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="edbc9-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="edbc9-135">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="edbc9-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="edbc9-136">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="edbc9-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="edbc9-137">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="edbc9-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="edbc9-138">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="edbc9-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="edbc9-139">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="edbc9-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="edbc9-140">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="edbc9-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
