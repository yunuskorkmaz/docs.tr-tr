---
description: 'Daha fazla bilgi edinin: nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma (Visual Basic)'
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
ms.openlocfilehash: 2e47a584632f124a001617770aeae5104ef20abe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476221"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="419db-103">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="419db-103">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>

<span data-ttu-id="419db-104">Bir yordam bir parametreyi [ByRef](../../../language-reference/modifiers/byref.md)olarak bildiriyorsa Visual Basic, yordam kodunu çağıran koddaki bağımsız değişkeni temel alan programlama öğesine doğrudan başvuru olarak verir.</span><span class="sxs-lookup"><span data-stu-id="419db-104">If a procedure declares a parameter as [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="419db-105">Bu yordam, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="419db-105">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="419db-106">Bazı durumlarda, çağıran kod bu tür bir değişikliğe karşı korumak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="419db-106">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="419db-107">Yordamda karşılık gelen parametre [ByVal](../../../language-reference/modifiers/byval.md) ' i bildirerek, bir bağımsız değişkeni her zaman bir değişikliğe karşı koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="419db-107">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="419db-108">Belirli bir bağımsız değişkeni bazı durumlarda değiştirebilmek istiyorsanız, ancak başka bir deyişle, çağrı `ByRef` kodunun her çağrıda geçen mekanizmayı belirlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="419db-108">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="419db-109">Bunu değere göre iletmek için karşılık gelen bağımsız değişkeni parantez içine alarak veya başvuruya göre geçirmek için parantez içine almak için bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="419db-109">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="419db-110">Daha fazla bilgi için bkz. [nasıl yapılır: bağımsız değişkeni değere göre geçirilmesine zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="419db-110">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="419db-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="419db-111">Example</span></span>  

 <span data-ttu-id="419db-112">Aşağıdaki örnek, bir dizi değişkeni alan ve öğelerinde çalışan iki yordamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="419db-112">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="419db-113">`increase`Yordam her bir öğeye yalnızca bir tane ekler.</span><span class="sxs-lookup"><span data-stu-id="419db-113">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="419db-114">`replace`Yordam parametreye yeni bir dizi atar `a()` ve sonra her öğeye bir tane ekler.</span><span class="sxs-lookup"><span data-stu-id="419db-114">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="419db-115">Ancak, yeniden atama, çağıran koddaki temeldeki dizi değişkenini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="419db-115">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="419db-116">İlk `MsgBox` çağrı, "Artdıktan sonra (n): 11, 21, 31, 41" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="419db-116">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="419db-117">Dizi `n` bir başvuru türü olduğundan, `increase` geçirme mekanizması olsa bile üyelerini değiştirebilir `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="419db-117">Because the array `n` is a reference type, `increase` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="419db-118">İkinci `MsgBox` çağrı "yenisiyle değiştirildikten sonra (n): 11, 21, 31, 41" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="419db-118">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="419db-119">`n`Geçirildiğinden `ByVal` , `replace` `n` çağıran koddaki değişkeni kendisine yeni bir dizi atayarak değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="419db-119">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="419db-120">`replace`Yeni dizi örneğini oluşturur `k` ve yerel değişkene atarsa `a` , `n` çağıran kod tarafından geçirilen başvuruyu kaybeder.</span><span class="sxs-lookup"><span data-stu-id="419db-120">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="419db-121">Üyelerini değiştirdiğinde `a` , yalnızca yerel dizi `k` etkilenir.</span><span class="sxs-lookup"><span data-stu-id="419db-121">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="419db-122">Bu nedenle, `replace` çağıran koddaki dizi değerlerini artırmaz `n` .</span><span class="sxs-lookup"><span data-stu-id="419db-122">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="419db-123">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="419db-123">Compile the code</span></span>  

 <span data-ttu-id="419db-124">Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="419db-124">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="419db-125">Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="419db-125">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="419db-126">Bu, kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="419db-126">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="419db-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="419db-127">See also</span></span>

- [<span data-ttu-id="419db-128">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="419db-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="419db-129">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="419db-129">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="419db-130">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="419db-130">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="419db-131">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="419db-131">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="419db-132">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="419db-132">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="419db-133">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="419db-133">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="419db-134">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="419db-134">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="419db-135">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="419db-135">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="419db-136">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="419db-136">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="419db-137">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="419db-137">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
