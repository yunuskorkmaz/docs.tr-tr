---
title: "Nasıl yapılır: İşaretçi Değişkeninin Değerini Edinme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="150f1-102">Nasıl yapılır: İşaretçi Değişkeninin Değerini Edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="150f1-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="150f1-103">İşaretçi indirection işleci değişkeni için bir işaretçi işaret konumda almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="150f1-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="150f1-104">Şu biçimi ifade alır nerede `p` bir işaretçi türü:</span><span class="sxs-lookup"><span data-stu-id="150f1-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="150f1-105">İşaretçi türünün dışında herhangi bir türde bir ifade birli indirection işleci kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="150f1-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="150f1-106">Ayrıca, kendisine uygulanamıyor bir [void](../../../csharp/language-reference/keywords/void.md) işaretçi.</span><span class="sxs-lookup"><span data-stu-id="150f1-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="150f1-107">İndirection işleci uyguladığınızda bir [null](../../../csharp/language-reference/keywords/null.md) işaretçisi sonucu uygulamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="150f1-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="150f1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="150f1-108">Example</span></span>  
 <span data-ttu-id="150f1-109">Aşağıdaki örnekte, türünde bir değişken `char` farklı türlerde işaretçileri kullanılarak erişilir.</span><span class="sxs-lookup"><span data-stu-id="150f1-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="150f1-110">Unutmayın adresi `theChar` bir değişkene ayrılan fiziksel adresi değişebildiğinden gelen çalıştırma için Çalıştır ' farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="150f1-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 <span data-ttu-id="150f1-111">**TheChar değerini Z =**</span><span class="sxs-lookup"><span data-stu-id="150f1-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="150f1-112">**TheChar adresini 12F718 =**</span><span class="sxs-lookup"><span data-stu-id="150f1-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="150f1-113">**PChar değerini Z =** </span><span class="sxs-lookup"><span data-stu-id="150f1-113">**Value of pChar = Z** </span></span>  
<span data-ttu-id="150f1-114">**PInt değerini 90 =**</span><span class="sxs-lookup"><span data-stu-id="150f1-114">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="150f1-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="150f1-115">See Also</span></span>  
 [<span data-ttu-id="150f1-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="150f1-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="150f1-117">İşaretçi ifadeleri</span><span class="sxs-lookup"><span data-stu-id="150f1-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="150f1-118">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="150f1-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="150f1-119">Türler</span><span class="sxs-lookup"><span data-stu-id="150f1-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="150f1-120">güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="150f1-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="150f1-121">fixed deyimi</span><span class="sxs-lookup"><span data-stu-id="150f1-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="150f1-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="150f1-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
