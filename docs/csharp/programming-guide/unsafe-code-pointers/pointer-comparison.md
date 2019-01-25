---
title: İşaretçi karşılaştırması - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: a2cbbabdad1d79c82bb5b3ec02a391727e552c98
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718643"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="5dcad-102">İşaretçi Karşılaştırması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5dcad-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="5dcad-103">Herhangi bir türde işaretçileri karşılaştırmak için aşağıdaki işleçleri uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5dcad-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="5dcad-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="5dcad-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="5dcad-105">İşaretsiz tamsayılar olarak varsa adresleri iki işlenenden Karşılaştırma işleçleri karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="5dcad-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dcad-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5dcad-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="5dcad-107">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="5dcad-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="5dcad-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dcad-108">See also</span></span>

- [<span data-ttu-id="5dcad-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5dcad-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5dcad-110">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="5dcad-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="5dcad-111">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5dcad-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="5dcad-112">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="5dcad-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="5dcad-113">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="5dcad-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="5dcad-114">Türler</span><span class="sxs-lookup"><span data-stu-id="5dcad-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="5dcad-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="5dcad-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="5dcad-116">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="5dcad-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="5dcad-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="5dcad-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
