---
title: 'Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme'
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
ms.openlocfilehash: deac87ca4690990a4d00f63d0ea9b843c3f9a9c4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344484"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="2fcc0-102">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fcc0-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="2fcc0-103">Bir yordamı çağırdığınızda, sağladığınız her bağımsız değişken yordamda tanımlanan parametrelerden birine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="2fcc0-104">Bazı durumlarda, yordam kodu, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="2fcc0-105">Diğer durumlarda yordam, bir bağımsız değişkenin yalnızca yerel kopyasını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="2fcc0-106">Yordamı çağırdığınızda Visual Basic, [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)' ı geçen her bağımsız değişkenin yerel bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="2fcc0-107">[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)olarak geçen her bir bağımsız değişken için, Visual Basic yordam koduna, çağıran koddaki bağımsız değişkeni temel alan programlama öğesine doğrudan başvuru verir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="2fcc0-108">Çağıran koddaki temeldeki öğe değiştirilebilir bir öğedir ve bağımsız değişken `ByRef`geçirilirse, yordam kodu doğrudan başvuruyu, çağıran koddaki öğenin değerini değiştirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="2fcc0-109">Temel alınan değeri değiştirme</span><span class="sxs-lookup"><span data-stu-id="2fcc0-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="2fcc0-110">Çağıran koddaki yordam bağımsız değişkeninin temel alınan değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="2fcc0-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="2fcc0-111">Yordam bildiriminde, bağımsız değişkenine karşılık gelen parametre için [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) belirtin.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="2fcc0-112">Çağıran kodda bağımsız değişken olarak değiştirilebilir bir programlama öğesi geçirin.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="2fcc0-113">Çağıran kodda bağımsız değişkeni parantez içine bağımsız değişken listesine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="2fcc0-114">Yordam kodunda, çağıran koddaki temel alınan öğeye bir değer atamak için parametre adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="2fcc0-115">Tanıtım için örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="2fcc0-116">Yerel kopyaları değiştirme</span><span class="sxs-lookup"><span data-stu-id="2fcc0-116">Changing Local Copies</span></span>  
 <span data-ttu-id="2fcc0-117">Çağıran koddaki temeldeki öğe değiştirilemeyen bir öğe ise veya bağımsız değişken `ByVal`geçirilirse yordam, çağıran koddaki değerini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="2fcc0-118">Ancak yordam, böyle bir bağımsız değişkenin yerel kopyasını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="2fcc0-119">Yordam kodundaki yordam bağımsız değişkeninin kopyasını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="2fcc0-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="2fcc0-120">Yordam bildiriminde, bağımsız değişkenine karşılık gelen parametre için [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) belirtin.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="2fcc0-121">veya</span><span class="sxs-lookup"><span data-stu-id="2fcc0-121">-or-</span></span>  
  
     <span data-ttu-id="2fcc0-122">Çağıran kodda bağımsız değişkenini bağımsız değişken listesinde parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="2fcc0-123">Bu, karşılık gelen parametre `ByRef`belirtse bile bağımsız değişkenini değere göre geçirmeye zorlar Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="2fcc0-124">Yordam kodunda, bağımsız değişkenin yerel kopyasına bir değer atamak için parametre adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="2fcc0-125">Çağıran koddaki temel alınan değer değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fcc0-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="2fcc0-126">Example</span></span>  
 <span data-ttu-id="2fcc0-127">Aşağıdaki örnek, bir dizi değişkeni alan ve öğelerinde çalışan iki yordamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="2fcc0-128">`increase` yordamı her bir öğeye yalnızca bir tane ekler.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="2fcc0-129">`replace` yordamı parametre `a()` yeni bir dizi atar ve sonra her öğeye bir tane ekler.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="2fcc0-130">İlk `MsgBox` çağrısı, "artdıktan sonra (n): 11, 21, 31, 41" olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="2fcc0-131">Dizi `n` bir başvuru türü olduğundan, `replace`, geçirme mekanizması `ByVal`olmasına rağmen üyelerini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="2fcc0-132">İkinci `MsgBox` çağrısı "yenisiyle değiştirildikten sonra (n): 101, 201, 301" olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="2fcc0-133">`n` `ByRef`geçirildiğinden `replace`, çağıran koddaki `n` değişkenini değiştirebilir ve buna yeni bir dizi atayabilir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="2fcc0-134">`n` bir başvuru türü olduğundan, `replace` üyelerini de değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="2fcc0-135">Yordamın, çağıran koddaki değişkenin kendisini değiştirmesini engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="2fcc0-136">Bkz. [nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="2fcc0-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="2fcc0-137">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="2fcc0-137">Compile the code</span></span>  
 <span data-ttu-id="2fcc0-138">Bir değişkeni başvuruya göre geçirdiğinizde, bu mekanizmayı belirtmek için `ByRef` anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="2fcc0-139">Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="2fcc0-140">Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="2fcc0-141">Bu, kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2fcc0-142">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="2fcc0-142">.NET Framework Security</span></span>  
 <span data-ttu-id="2fcc0-143">Bir yordamın, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin vermek için her zaman potansiyel bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="2fcc0-144">Bu değerin değiştirilmesini beklediğinizden ve kullanılmadan önce geçerliliği göz önünde denetlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fcc0-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fcc0-145">See also</span></span>

- [<span data-ttu-id="2fcc0-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2fcc0-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2fcc0-147">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="2fcc0-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2fcc0-148">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="2fcc0-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="2fcc0-149">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="2fcc0-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="2fcc0-150">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="2fcc0-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="2fcc0-151">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="2fcc0-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="2fcc0-152">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="2fcc0-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="2fcc0-153">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="2fcc0-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="2fcc0-154">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="2fcc0-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="2fcc0-155">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="2fcc0-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
