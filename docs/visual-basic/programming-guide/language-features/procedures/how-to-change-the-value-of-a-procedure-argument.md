---
title: "Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)"
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
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba23c8f0b4b0b6e751546019af902a6305b9ef53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="ec8d7-102">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec8d7-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="ec8d7-103">Bir yordam çağrısı, sağladığınız her bağımsız değişkeni yordamda tanımlanan parametrelerin birine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="ec8d7-104">Bazı durumlarda, yordam kodunu çağıran kodu bir bağımsız değişken temel değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="ec8d7-105">Diğer durumlarda, yordam bir bağımsız değişken yalnızca kendi yerel kopyasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="ec8d7-106">Yordam çağırdığınızda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] geçirilen her bağımsız değişkeni yerel bir kopyasını oluşturur [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="ec8d7-106">When you call the procedure, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="ec8d7-107">Her değişken için [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yordamı kod çağıran kodu değişkeninde temel programlama öğesi için doğrudan bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="ec8d7-108">Çağrıyı yapan kod temel alınan öğe değiştirilebilir bir öğedir ve bağımsız değişken geçirildi `ByRef`, yordam kodu çağıran kodu öğenin değerini değiştirmek için doğrudan başvuru kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="ec8d7-109">Temel alınan değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="ec8d7-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="ec8d7-110">Temel alınan arama kodda bir yordam bağımsız değişkeninin değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="ec8d7-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="ec8d7-111">Yordam bildiriminde belirtin [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bağımsız değişkeni için karşılık gelen parametresi için.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="ec8d7-112">Arama kodda değiştirilebilir bir programlama öğesi bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="ec8d7-113">Arama kodda bağımsız değişken bağımsız değişken listesinde parantez içine almayın.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="ec8d7-114">Yordam kodunda parametre adı çağıran kodu temel alınan öğe için bir değer atamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="ec8d7-115">Örnek bir örnek için aşağı daha fazla.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="ec8d7-116">Yerel kopyaları değiştirme</span><span class="sxs-lookup"><span data-stu-id="ec8d7-116">Changing Local Copies</span></span>  
 <span data-ttu-id="ec8d7-117">Çağrıyı yapan kod temel alınan öğe değiştirilemez bir öğeyse ya da bağımsız değişken geçirildi `ByVal`, yordamı çağıran kodu değeriyle değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="ec8d7-118">Ancak, yordam böyle bir bağımsız değişken yerel kopyasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="ec8d7-119">Bir yordam bağımsız değişkenini yordamı kodda kopyasını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="ec8d7-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="ec8d7-120">Yordam bildiriminde belirtin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) bağımsız değişkeni için karşılık gelen parametresi için.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="ec8d7-121">veya</span><span class="sxs-lookup"><span data-stu-id="ec8d7-121">-or-</span></span>  
  
     <span data-ttu-id="ec8d7-122">Çağrıyı yapan kod içinde bağımsız değişken bağımsız değişken listesinde parantez içinde alın.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="ec8d7-123">Bu zorlar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] karşılık gelen bir parametre belirtse dahi bağımsız değişkeni değere göre geçirilecek `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-123">This forces [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="ec8d7-124">Yordam kodunda parametre adı yerel kopyasını bağımsız değişkeni için bir değer atamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="ec8d7-125">Çağrıyı yapan kod temel alınan değer değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec8d7-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec8d7-126">Example</span></span>  
 <span data-ttu-id="ec8d7-127">Aşağıdaki örnek, bir dizi değişkeni alabilir ve çalışan iki yordam üzerinde öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="ec8d7-128">`increase` Yordamı yalnızca ekler her öğe için.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="ec8d7-129">`replace` Yordamı atar yeni bir dizi parametre `a()` ve her öğe için ekler.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 <span data-ttu-id="ec8d7-130">İlk `MsgBox` çağrısı görüntüler "increase(n) sonra: 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="ec8d7-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="ec8d7-131">Çünkü dizi `n` bir başvuru türü `replace` geçirme mekanizması olmamasına rağmen bu grubun üyeleri değiştirebilirsiniz `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="ec8d7-132">İkinci `MsgBox` çağrısı görüntüler "replace(n) sonra: 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="ec8d7-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="ec8d7-133">Çünkü `n` geçirilen `ByRef`, `replace` değişkeni değiştirebilirsiniz `n` çağıran kodu ve ata ona yeni bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="ec8d7-134">Çünkü `n` bir başvuru türü `replace` üyelerini de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="ec8d7-135">Çağrıyı yapan kod değişkenin kendisine değiştirme yordamı engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="ec8d7-136">Bkz: [nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ec8d7-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ec8d7-137">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ec8d7-137">Compiling the Code</span></span>  
 <span data-ttu-id="ec8d7-138">Başvuruya göre bir değişken geçirdiğinizde kullanmalısınız `ByRef` anahtar Bu mekanizma belirtin.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="ec8d7-139">Varsayılan olarak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bağımsız değişkenleri değere göre geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-139">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="ec8d7-140">Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="ec8d7-141">Bu, kodunuzu okumak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ec8d7-142">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ec8d7-142">.NET Framework Security</span></span>  
 <span data-ttu-id="ec8d7-143">Yoktur her zaman potansiyel bir risk çağıran kodu bir bağımsız değişken alttaki değerini değiştirmek bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="ec8d7-144">Bu değeri değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec8d7-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec8d7-145">See Also</span></span>  
 [<span data-ttu-id="ec8d7-146">Yordamları</span><span class="sxs-lookup"><span data-stu-id="ec8d7-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="ec8d7-147">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ec8d7-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ec8d7-148">Nasıl yapılır: bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="ec8d7-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="ec8d7-149">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="ec8d7-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="ec8d7-150">Değiştirilebilir ve değiştirilemez bağımsız değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="ec8d7-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="ec8d7-151">Değere ve başvuruya göre bağımsız değişken geçirme arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="ec8d7-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="ec8d7-152">Nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma</span><span class="sxs-lookup"><span data-stu-id="ec8d7-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="ec8d7-153">Nasıl yapılır: bağımsız değişkeni değere göre geçirilecek şekilde zorlama</span><span class="sxs-lookup"><span data-stu-id="ec8d7-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="ec8d7-154">Bağımsız değişkenleri konuma göre ve ada göre geçirme</span><span class="sxs-lookup"><span data-stu-id="ec8d7-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="ec8d7-155">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="ec8d7-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
