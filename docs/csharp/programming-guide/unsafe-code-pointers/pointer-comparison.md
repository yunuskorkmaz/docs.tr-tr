---
title: İşaretçi karşılaştırması - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 5185bd5e1686858452efcc7c89e2c1977e094386
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969212"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="9ebef-102">İşaretçi Karşılaştırması (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9ebef-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="9ebef-103">Herhangi bir türde işaretçileri karşılaştırmak için aşağıdaki işleçleri uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9ebef-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="9ebef-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="9ebef-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="9ebef-105">İşaretsiz tamsayılar olarak varsa adresleri iki işlenenden Karşılaştırma işleçleri karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="9ebef-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ebef-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ebef-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a><span data-ttu-id="9ebef-107">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="9ebef-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="9ebef-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ebef-108">See also</span></span>

- [<span data-ttu-id="9ebef-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9ebef-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9ebef-110">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9ebef-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="9ebef-111">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9ebef-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="9ebef-112">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="9ebef-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="9ebef-113">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="9ebef-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="9ebef-114">Türler</span><span class="sxs-lookup"><span data-stu-id="9ebef-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="9ebef-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="9ebef-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="9ebef-116">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="9ebef-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="9ebef-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="9ebef-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
