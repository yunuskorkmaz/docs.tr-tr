---
title: İşaretçi karşılaştırması - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 72d9017064959c801bd2702ff585ee16b1592da6
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236797"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="3207d-102">İşaretçi Karşılaştırması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3207d-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="3207d-103">Herhangi bir türde işaretçileri karşılaştırmak için aşağıdaki işleçleri uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3207d-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="3207d-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="3207d-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="3207d-105">İşaretsiz tamsayılar olarak varsa adresleri iki işlenenden Karşılaştırma işleçleri karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="3207d-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3207d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3207d-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="3207d-107">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="3207d-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="3207d-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3207d-108">See Also</span></span>

- [<span data-ttu-id="3207d-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3207d-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3207d-110">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="3207d-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="3207d-111">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3207d-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="3207d-112">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="3207d-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="3207d-113">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="3207d-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="3207d-114">Türler</span><span class="sxs-lookup"><span data-stu-id="3207d-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="3207d-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="3207d-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="3207d-116">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="3207d-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="3207d-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="3207d-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
