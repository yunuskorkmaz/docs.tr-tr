---
title: İşaretçi Karşılaştırması (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: fa980c944159c477c333762ffad569332fba9402
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086645"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="aa663-102">İşaretçi Karşılaştırması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="aa663-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="aa663-103">Herhangi bir türde işaretçileri karşılaştırmak için aşağıdaki işleçleri uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aa663-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="aa663-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="aa663-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="aa663-105">İşaretsiz tamsayılar olarak varsa adresleri iki işlenenden Karşılaştırma işleçleri karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="aa663-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa663-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa663-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="aa663-107">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="aa663-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="aa663-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa663-108">See Also</span></span>

- [<span data-ttu-id="aa663-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa663-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aa663-110">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="aa663-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="aa663-111">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="aa663-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="aa663-112">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="aa663-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="aa663-113">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="aa663-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="aa663-114">Türler</span><span class="sxs-lookup"><span data-stu-id="aa663-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="aa663-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="aa663-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="aa663-116">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="aa663-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="aa663-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="aa663-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
