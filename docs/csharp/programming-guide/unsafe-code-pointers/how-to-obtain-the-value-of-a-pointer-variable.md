---
title: 'Nasıl yapılır: - işaretçi değişkeninin değerini edinme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 288d8cb2d286f55cc9a162614d45ef7b298f79f1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974490"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="e4c26-102">Nasıl yapılır: işaretçi değişkeninin değerini edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e4c26-102">How to: obtain the value of a pointer variable (C# Programming Guide)</span></span>

<span data-ttu-id="e4c26-103">İşaretçi yöneltme işleci için bir işaretçi tarafından işaret edilen konumda bir değişkeni almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4c26-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="e4c26-104">İfade, aşağıdaki biçimi alır burada `p` bir işaretçi türü:</span><span class="sxs-lookup"><span data-stu-id="e4c26-104">The expression takes the following form, where `p` is a pointer type:</span></span>  

```csharp
*p;  
```

<span data-ttu-id="e4c26-105">İşaretçi türünün dışındaki herhangi bir türde bir ifade üzerinde birli yöneltme işlecini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e4c26-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="e4c26-106">Ayrıca, kendisine uygulanamıyor bir [void](../../../csharp/language-reference/keywords/void.md) işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e4c26-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  

<span data-ttu-id="e4c26-107">Yöneltme işleci uygulandığında bir [null](../../../csharp/language-reference/keywords/null.md) işaretçisi sonucu uygulamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4c26-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  

## <a name="example"></a><span data-ttu-id="e4c26-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4c26-108">Example</span></span>

<span data-ttu-id="e4c26-109">Aşağıdaki örnekte, türünde bir değişken `char` farklı türlerde işaretçiler kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e4c26-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="e4c26-110">Unutmayın adresini `theChar` gelen çalıştıracak çalışma için bir değişkene ayrılan fiziksel adresi geçebileceğiniz farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4c26-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
<span data-ttu-id="e4c26-111">**TheChar değerini Z =**</span><span class="sxs-lookup"><span data-stu-id="e4c26-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="e4c26-112">**TheChar adresini 12F718 =**</span><span class="sxs-lookup"><span data-stu-id="e4c26-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="e4c26-113">**PChar değerini Z =**</span><span class="sxs-lookup"><span data-stu-id="e4c26-113">**Value of pChar = Z**</span></span>  
<span data-ttu-id="e4c26-114">**PInt değerini 90 =**</span><span class="sxs-lookup"><span data-stu-id="e4c26-114">**Value of pInt = 90**</span></span>  

## <a name="see-also"></a><span data-ttu-id="e4c26-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4c26-115">See also</span></span>

- [<span data-ttu-id="e4c26-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e4c26-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e4c26-117">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="e4c26-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="e4c26-118">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="e4c26-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e4c26-119">Türler</span><span class="sxs-lookup"><span data-stu-id="e4c26-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="e4c26-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="e4c26-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="e4c26-121">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="e4c26-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="e4c26-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="e4c26-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
