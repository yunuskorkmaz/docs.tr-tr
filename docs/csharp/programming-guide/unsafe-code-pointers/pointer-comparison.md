---
title: "İşaretçi Karşılaştırması (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0b45b9152272244b9a0c9d0fa3787973f8f8182a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="04517-102">İşaretçi Karşılaştırması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="04517-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="04517-103">Herhangi bir türde işaretçileri karşılaştırmak için aşağıdaki işleçleri uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="04517-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="04517-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="04517-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="04517-105">Karşılaştırma işleçleri imzasız tamsayılar varsa gibi iki işlenen adreslerini karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="04517-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04517-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="04517-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="04517-107">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="04517-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="04517-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04517-108">See Also</span></span>  
 [<span data-ttu-id="04517-109">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="04517-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="04517-110">İşaretçi ifadeleri</span><span class="sxs-lookup"><span data-stu-id="04517-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="04517-111">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="04517-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="04517-112">İşaretçileri işleme</span><span class="sxs-lookup"><span data-stu-id="04517-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="04517-113">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="04517-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="04517-114">Türler</span><span class="sxs-lookup"><span data-stu-id="04517-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="04517-115">güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="04517-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="04517-116">fixed deyimi</span><span class="sxs-lookup"><span data-stu-id="04517-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="04517-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="04517-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
