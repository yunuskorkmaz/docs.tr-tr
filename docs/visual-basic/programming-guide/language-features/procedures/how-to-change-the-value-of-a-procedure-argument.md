---
title: 'Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)'
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
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 93d9cc11e919e45fdd3b48dd2731b165f3466640
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="78a24-102">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78a24-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="78a24-103">Bir yordam çağrısı, sağladığınız her bağımsız değişkeni yordamda tanımlanan parametrelerin birine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="78a24-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="78a24-104">Bazı durumlarda, yordam kodunu çağıran kodu bir bağımsız değişken temel değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78a24-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="78a24-105">Diğer durumlarda, yordam bir bağımsız değişken yalnızca kendi yerel kopyasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78a24-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="78a24-106">Yordam çağrısı, Visual Basic geçirilen her bağımsız değişkeni yerel bir kopyasını oluşturur [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="78a24-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="78a24-107">Her değişken için [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic yordamı kod çağıran kodu değişkeninde temel programlama öğesi için doğrudan bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="78a24-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="78a24-108">Çağrıyı yapan kod temel alınan öğe değiştirilebilir bir öğedir ve bağımsız değişken geçirildi `ByRef`, yordam kodu çağıran kodu öğenin değerini değiştirmek için doğrudan başvuru kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78a24-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="78a24-109">Temel alınan değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="78a24-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="78a24-110">Temel alınan arama kodda bir yordam bağımsız değişkeninin değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="78a24-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="78a24-111">Yordam bildiriminde belirtin [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bağımsız değişkeni için karşılık gelen parametresi için.</span><span class="sxs-lookup"><span data-stu-id="78a24-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="78a24-112">Arama kodda değiştirilebilir bir programlama öğesi bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="78a24-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="78a24-113">Arama kodda bağımsız değişken bağımsız değişken listesinde parantez içine almayın.</span><span class="sxs-lookup"><span data-stu-id="78a24-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="78a24-114">Yordam kodunda parametre adı çağıran kodu temel alınan öğe için bir değer atamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="78a24-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="78a24-115">Örnek bir örnek için aşağı daha fazla.</span><span class="sxs-lookup"><span data-stu-id="78a24-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="78a24-116">Yerel kopyaları değiştirme</span><span class="sxs-lookup"><span data-stu-id="78a24-116">Changing Local Copies</span></span>  
 <span data-ttu-id="78a24-117">Çağrıyı yapan kod temel alınan öğe değiştirilemez bir öğeyse ya da bağımsız değişken geçirildi `ByVal`, yordamı çağıran kodu değeriyle değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="78a24-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="78a24-118">Ancak, yordam böyle bir bağımsız değişken yerel kopyasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78a24-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="78a24-119">Bir yordam bağımsız değişkenini yordamı kodda kopyasını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="78a24-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="78a24-120">Yordam bildiriminde belirtin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) bağımsız değişkeni için karşılık gelen parametresi için.</span><span class="sxs-lookup"><span data-stu-id="78a24-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="78a24-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="78a24-121">-or-</span></span>  
  
     <span data-ttu-id="78a24-122">Çağrıyı yapan kod içinde bağımsız değişken bağımsız değişken listesinde parantez içinde alın.</span><span class="sxs-lookup"><span data-stu-id="78a24-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="78a24-123">Karşılık gelen bir parametre belirtir olsa bile bu bağımsız değişkeni değere göre geçirilecek Visual Basic zorlar `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="78a24-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="78a24-124">Yordam kodunda parametre adı yerel kopyasını bağımsız değişkeni için bir değer atamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="78a24-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="78a24-125">Çağrıyı yapan kod temel alınan değer değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="78a24-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78a24-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="78a24-126">Example</span></span>  
 <span data-ttu-id="78a24-127">Aşağıdaki örnek, bir dizi değişkeni alabilir ve çalışan iki yordam üzerinde öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="78a24-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="78a24-128">`increase` Yordamı yalnızca ekler her öğe için.</span><span class="sxs-lookup"><span data-stu-id="78a24-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="78a24-129">`replace` Yordamı atar yeni bir dizi parametre `a()` ve her öğe için ekler.</span><span class="sxs-lookup"><span data-stu-id="78a24-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 <span data-ttu-id="78a24-130">İlk `MsgBox` çağrısı görüntüler "increase(n) sonra: 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="78a24-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="78a24-131">Çünkü dizi `n` bir başvuru türü `replace` geçirme mekanizması olmamasına rağmen bu grubun üyeleri değiştirebilirsiniz `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="78a24-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="78a24-132">İkinci `MsgBox` çağrısı görüntüler "replace(n) sonra: 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="78a24-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="78a24-133">Çünkü `n` geçirilen `ByRef`, `replace` değişkeni değiştirebilirsiniz `n` çağıran kodu ve ata ona yeni bir dizi.</span><span class="sxs-lookup"><span data-stu-id="78a24-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="78a24-134">Çünkü `n` bir başvuru türü `replace` üyelerini de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78a24-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="78a24-135">Çağrıyı yapan kod değişkenin kendisine değiştirme yordamı engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="78a24-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="78a24-136">Bkz: [nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="78a24-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78a24-137">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="78a24-137">Compiling the Code</span></span>  
 <span data-ttu-id="78a24-138">Başvuruya göre bir değişken geçirdiğinizde kullanmalısınız `ByRef` anahtar Bu mekanizma belirtin.</span><span class="sxs-lookup"><span data-stu-id="78a24-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="78a24-139">Visual Basic'de bağımsız değişkenleri değere göre geçirilecek varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="78a24-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="78a24-140">Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="78a24-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="78a24-141">Bu, kodunuzu okumak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="78a24-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="78a24-142">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="78a24-142">.NET Framework Security</span></span>  
 <span data-ttu-id="78a24-143">Yoktur her zaman potansiyel bir risk çağıran kodu bir bağımsız değişken alttaki değerini değiştirmek bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="78a24-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="78a24-144">Bu değeri değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="78a24-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a24-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78a24-145">See Also</span></span>  
 [<span data-ttu-id="78a24-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="78a24-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="78a24-147">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="78a24-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="78a24-148">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="78a24-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="78a24-149">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="78a24-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="78a24-150">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="78a24-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="78a24-151">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="78a24-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="78a24-152">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="78a24-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="78a24-153">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="78a24-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="78a24-154">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="78a24-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="78a24-155">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="78a24-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
