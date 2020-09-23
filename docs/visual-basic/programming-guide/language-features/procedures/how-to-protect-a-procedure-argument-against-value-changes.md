---
title: 'Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma'
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
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 84eadf3d364b69120221d80e464b1175b1602e13
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071488"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="94bab-102">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94bab-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>

<span data-ttu-id="94bab-103">Bir yordam bir parametreyi [ByRef](../../../language-reference/modifiers/byref.md)olarak bildiriyorsa Visual Basic, yordam kodunu çağıran koddaki bağımsız değişkeni temel alan programlama öğesine doğrudan başvuru olarak verir.</span><span class="sxs-lookup"><span data-stu-id="94bab-103">If a procedure declares a parameter as [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="94bab-104">Bu yordam, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="94bab-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="94bab-105">Bazı durumlarda, çağıran kod bu tür bir değişikliğe karşı korumak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="94bab-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="94bab-106">Yordamda karşılık gelen parametre [ByVal](../../../language-reference/modifiers/byval.md) ' i bildirerek, bir bağımsız değişkeni her zaman bir değişikliğe karşı koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94bab-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="94bab-107">Belirli bir bağımsız değişkeni bazı durumlarda değiştirebilmek istiyorsanız, ancak başka bir deyişle, çağrı `ByRef` kodunun her çağrıda geçen mekanizmayı belirlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94bab-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="94bab-108">Bunu değere göre iletmek için karşılık gelen bağımsız değişkeni parantez içine alarak veya başvuruya göre geçirmek için parantez içine almak için bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="94bab-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="94bab-109">Daha fazla bilgi için bkz. [nasıl yapılır: bağımsız değişkeni değere göre geçirilmesine zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="94bab-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94bab-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="94bab-110">Example</span></span>  

 <span data-ttu-id="94bab-111">Aşağıdaki örnek, bir dizi değişkeni alan ve öğelerinde çalışan iki yordamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="94bab-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="94bab-112">`increase`Yordam her bir öğeye yalnızca bir tane ekler.</span><span class="sxs-lookup"><span data-stu-id="94bab-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="94bab-113">`replace`Yordam parametreye yeni bir dizi atar `a()` ve sonra her öğeye bir tane ekler.</span><span class="sxs-lookup"><span data-stu-id="94bab-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="94bab-114">Ancak, yeniden atama, çağıran koddaki temeldeki dizi değişkenini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="94bab-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="94bab-115">İlk `MsgBox` çağrı, "Artdıktan sonra (n): 11, 21, 31, 41" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="94bab-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="94bab-116">Dizi `n` bir başvuru türü olduğundan, `increase` geçirme mekanizması olsa bile üyelerini değiştirebilir `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="94bab-116">Because the array `n` is a reference type, `increase` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="94bab-117">İkinci `MsgBox` çağrı "yenisiyle değiştirildikten sonra (n): 11, 21, 31, 41" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="94bab-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="94bab-118">`n`Geçirildiğinden `ByVal` , `replace` `n` çağıran koddaki değişkeni kendisine yeni bir dizi atayarak değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="94bab-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="94bab-119">`replace`Yeni dizi örneğini oluşturur `k` ve yerel değişkene atarsa `a` , `n` çağıran kod tarafından geçirilen başvuruyu kaybeder.</span><span class="sxs-lookup"><span data-stu-id="94bab-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="94bab-120">Üyelerini değiştirdiğinde `a` , yalnızca yerel dizi `k` etkilenir.</span><span class="sxs-lookup"><span data-stu-id="94bab-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="94bab-121">Bu nedenle, `replace` çağıran koddaki dizi değerlerini artırmaz `n` .</span><span class="sxs-lookup"><span data-stu-id="94bab-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="94bab-122">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="94bab-122">Compile the code</span></span>  

 <span data-ttu-id="94bab-123">Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="94bab-123">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="94bab-124">Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="94bab-124">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="94bab-125">Bu, kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="94bab-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bab-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94bab-126">See also</span></span>

- [<span data-ttu-id="94bab-127">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="94bab-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="94bab-128">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="94bab-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="94bab-129">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="94bab-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="94bab-130">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="94bab-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="94bab-131">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="94bab-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="94bab-132">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="94bab-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="94bab-133">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="94bab-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="94bab-134">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="94bab-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="94bab-135">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="94bab-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="94bab-136">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="94bab-136">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
