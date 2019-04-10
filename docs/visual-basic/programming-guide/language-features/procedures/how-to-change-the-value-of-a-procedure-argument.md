---
title: 'Nasıl yapılır: Bir yordam bağımsız değişkeninin (Visual Basic) değerini değiştirme'
ms.date: 07/20/2015
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
ms.openlocfilehash: a56bdf888163c9559b87e857abb33522c547ed45
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316628"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="281af-102">Nasıl yapılır: Bir yordam bağımsız değişkeninin (Visual Basic) değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="281af-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="281af-103">Bir yordamı çağırdığınızda, sağladığınız her bağımsız değişken yordamda tanımlanan parametrelerin birine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="281af-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="281af-104">Bazı durumlarda çağıran koddaki bağımsız değişken temel değer yordamının kodunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="281af-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="281af-105">Diğer durumlarda, yordam bir bağımsız değişken yalnızca yerel kopyasına değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="281af-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="281af-106">Yordamı çağırdığınızda, Visual Basic geçirilen her bağımsız değişken yerel bir kopyasını oluşturur. [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="281af-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="281af-107">Geçirilen her bağımsız değişken için [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic programlama öğesine çağıran koddaki bağımsız değişken arka plandaki bir doğrudan başvuru yordamının kodunu verir.</span><span class="sxs-lookup"><span data-stu-id="281af-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="281af-108">Temel alınan öğe çağıran koddaki değiştirilebilir bir öğedir ve geçirilen bağımsız değişken `ByRef`, yordam kodu doğrudan başvuruyu çağıran koddaki öğenin değerini değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="281af-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="281af-109">Temeldeki değeri değiştirme</span><span class="sxs-lookup"><span data-stu-id="281af-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="281af-110">Temel alınan çağıran koddaki bir yordam bağımsız değişkeninin değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="281af-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="281af-111">Yordam bildiriminde belirtin [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) için argument'ine karşılık gelen parametre.</span><span class="sxs-lookup"><span data-stu-id="281af-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="281af-112">Çağıran kod içinde değiştirilebilir bir programlama öğesine bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="281af-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="281af-113">Çağıran kod içinde bağımsız değişken bağımsız değişken listesinde parantez içine almayın.</span><span class="sxs-lookup"><span data-stu-id="281af-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="281af-114">Yordam kodunda parametre adı çağıran koddaki temel öğeye bir değer atamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="281af-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="281af-115">Örnek görmek için bir tanıtım daha ilerisine.</span><span class="sxs-lookup"><span data-stu-id="281af-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="281af-116">Yerel kopya değiştirme</span><span class="sxs-lookup"><span data-stu-id="281af-116">Changing Local Copies</span></span>  
 <span data-ttu-id="281af-117">Temel alınan öğe çağıran koddaki değiştirilemez bir öğe ise veya bağımsız değişken geçirilmezse `ByVal`, yordamı çağıran koddaki değerini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="281af-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="281af-118">Ancak, yordam böyle bir bağımsız değişken yerel kopyasına değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="281af-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="281af-119">Yordam kodunda bir yordam bağımsız değişkeninin kopyasını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="281af-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="281af-120">Yordam bildiriminde belirtin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) için argument'ine karşılık gelen parametre.</span><span class="sxs-lookup"><span data-stu-id="281af-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="281af-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="281af-121">-or-</span></span>  
  
     <span data-ttu-id="281af-122">Çağıran kod içinde bağımsız değişken bağımsız değişken listesinde parantez içinde alın.</span><span class="sxs-lookup"><span data-stu-id="281af-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="281af-123">Karşılık gelen parametre belirtse dahi, bu bağımsız değişkeni değere göre geçirilecek Visual Basic zorlar `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="281af-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="281af-124">Yordam kodunda parametre adı bağımsız değişkeni bir yerel kopyasını için bir değer atamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="281af-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="281af-125">Temeldeki değeri çağıran koddaki değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="281af-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="281af-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="281af-126">Example</span></span>  
 <span data-ttu-id="281af-127">Aşağıdaki örnek, bir dizi değişkenini alabilir ve çalışan iki yordamı öğeleri üzerinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="281af-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="281af-128">`increase` Yordamı yalnızca ekler her öğe için.</span><span class="sxs-lookup"><span data-stu-id="281af-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="281af-129">`replace` Yordamı yeni bir dizi parametresine atar `a()` ve sonra her öğeye ekler.</span><span class="sxs-lookup"><span data-stu-id="281af-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="281af-130">İlk `MsgBox` çağrı görüntüler "increase(n) sonra: 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="281af-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="281af-131">Çünkü dizi `n` bir başvuru türüdür `replace` geçirme mekanizmasını olsa bile, bu grubun üyeleri değiştirebilirsiniz `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="281af-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="281af-132">İkinci `MsgBox` çağrı görüntüler "replace(n) sonra: 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="281af-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="281af-133">Çünkü `n` geçirilen `ByRef`, `replace` değişkeni değiştirebilirsiniz `n` çağıran kod ve ona yeni bir dizi atayın.</span><span class="sxs-lookup"><span data-stu-id="281af-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="281af-134">Çünkü `n` bir başvuru türüdür `replace` üyelerini de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="281af-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="281af-135">Yordamı çağıran koddaki değişkenin kendisine değiştirmesini engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="281af-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="281af-136">Bkz: [nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="281af-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="281af-137">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="281af-137">Compiling the Code</span></span>  
 <span data-ttu-id="281af-138">Başvuruya göre değişken başarıyla sonuçlandıktan sonra kullanmalısınız `ByRef` Bu mekanizma belirtmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="281af-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="281af-139">Visual Basic'te bağımsız değişkenleri değere göre geçirilecek varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="281af-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="281af-140">Ancak, iyi bir ya da içerecek şekilde programlama [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğü ile bildirilen her parametre.</span><span class="sxs-lookup"><span data-stu-id="281af-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="281af-141">Bu, kodunuzu daha kolay okunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="281af-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="281af-142">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="281af-142">.NET Framework Security</span></span>  
 <span data-ttu-id="281af-143">Her zaman bir olası riski yoktur çağıran koddaki bağımsız değişken temel değeri değiştirmek bir yordam vermek.</span><span class="sxs-lookup"><span data-stu-id="281af-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="281af-144">Bu değer, değiştirilmesi ve kullanmadan önce geçerliliğini denetlemek için hazırlanması beklediğiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="281af-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="281af-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="281af-145">See also</span></span>

- [<span data-ttu-id="281af-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="281af-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="281af-147">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="281af-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="281af-148">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="281af-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="281af-149">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="281af-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="281af-150">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="281af-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="281af-151">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="281af-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="281af-152">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="281af-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="281af-153">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="281af-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="281af-154">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="281af-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="281af-155">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="281af-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
