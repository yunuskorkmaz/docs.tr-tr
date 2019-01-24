---
title: 'Nasıl yapılır: -İşaretçi değişkeninin değerini edinme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 5fbc925b6770bc951a0d7ec856898f62c265462e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577160"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="32ffc-102">Nasıl yapılır: İşaretçi değişkeninin değerini edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="32ffc-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="32ffc-103">İşaretçi yöneltme işleci için bir işaretçi tarafından işaret edilen konumda bir değişkeni almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="32ffc-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="32ffc-104">İfade, aşağıdaki biçimi alır burada `p` bir işaretçi türü:</span><span class="sxs-lookup"><span data-stu-id="32ffc-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="32ffc-105">İşaretçi türünün dışındaki herhangi bir türde bir ifade üzerinde birli yöneltme işlecini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="32ffc-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="32ffc-106">Ayrıca, kendisine uygulanamıyor bir [void](../../../csharp/language-reference/keywords/void.md) işaretçi.</span><span class="sxs-lookup"><span data-stu-id="32ffc-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="32ffc-107">Yöneltme işleci uygulandığında bir [null](../../../csharp/language-reference/keywords/null.md) işaretçisi sonucu uygulamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="32ffc-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32ffc-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="32ffc-108">Example</span></span>  
 <span data-ttu-id="32ffc-109">Aşağıdaki örnekte, türünde bir değişken `char` farklı türlerde işaretçiler kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="32ffc-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="32ffc-110">Unutmayın adresini `theChar` gelen çalıştıracak çalışma için bir değişkene ayrılan fiziksel adresi geçebileceğiniz farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="32ffc-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
<span data-ttu-id="32ffc-111">**TheChar değerini Z =**
**theChar adresini 12F718 =**
**pChar değerini Z =**
**pInt değerini 90 =**</span><span class="sxs-lookup"><span data-stu-id="32ffc-111">**Value of theChar = Z**
**Address of theChar = 12F718**
**Value of pChar = Z**
**Value of pInt = 90**</span></span>

## <a name="see-also"></a><span data-ttu-id="32ffc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32ffc-112">See also</span></span>

- [<span data-ttu-id="32ffc-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="32ffc-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="32ffc-114">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="32ffc-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="32ffc-115">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="32ffc-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="32ffc-116">Türler</span><span class="sxs-lookup"><span data-stu-id="32ffc-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="32ffc-117">unsafe</span><span class="sxs-lookup"><span data-stu-id="32ffc-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="32ffc-118">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="32ffc-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="32ffc-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="32ffc-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
