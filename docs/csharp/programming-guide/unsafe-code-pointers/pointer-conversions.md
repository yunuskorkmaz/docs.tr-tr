---
title: "İşaretçi Dönüşümleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36589d139c91e04d9e3d8b31281a91c26b85a5d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="64441-102">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="64441-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="64441-103">Aşağıdaki tabloda önceden tanımlanmış örtük işaretçi dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="64441-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="64441-104">Örtük dönüşümler yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="64441-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="64441-105">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="64441-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="64441-106">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="64441-106">From</span></span>|<span data-ttu-id="64441-107">Bitiş</span><span class="sxs-lookup"><span data-stu-id="64441-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="64441-108">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="64441-108">Any pointer type</span></span>|<span data-ttu-id="64441-109">void \*</span><span class="sxs-lookup"><span data-stu-id="64441-109">void\*</span></span>|  
|<span data-ttu-id="64441-110">null</span><span class="sxs-lookup"><span data-stu-id="64441-110">null</span></span>|<span data-ttu-id="64441-111">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="64441-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="64441-112">Açık işaretçi dönüştürme var olduğu örtük dönüştürme, bir cast ifadesi kullanarak dönüşümlerini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64441-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="64441-113">Aşağıdaki tabloda bu dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="64441-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="64441-114">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="64441-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="64441-115">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="64441-115">From</span></span>|<span data-ttu-id="64441-116">Bitiş</span><span class="sxs-lookup"><span data-stu-id="64441-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="64441-117">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="64441-117">Any pointer type</span></span>|<span data-ttu-id="64441-118">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="64441-118">Any other pointer type</span></span>|  
|<span data-ttu-id="64441-119">sbyte, bayt, short, ushort, int, uint, uzun veya ulong</span><span class="sxs-lookup"><span data-stu-id="64441-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="64441-120">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="64441-120">Any pointer type</span></span>|  
|<span data-ttu-id="64441-121">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="64441-121">Any pointer type</span></span>|<span data-ttu-id="64441-122">sbyte, bayt, short, ushort, int, uint, uzun veya ulong</span><span class="sxs-lookup"><span data-stu-id="64441-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="64441-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="64441-123">Example</span></span>  
 <span data-ttu-id="64441-124">Aşağıdaki örnekte, bir işaretçi `int` gösteren bir işaretçi dönüştürülür `byte`.</span><span class="sxs-lookup"><span data-stu-id="64441-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="64441-125">İşaretçinin en düşük adresli bayta değişkenin işaret dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="64441-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="64441-126">Ne zaman, sırayla Artır boyutu kadar sonuç `int` (4 bayt), değişkenin kalan bayt sayısı görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64441-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="64441-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64441-127">See Also</span></span>  
 [<span data-ttu-id="64441-128">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="64441-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="64441-129">İşaretçi ifadeleri</span><span class="sxs-lookup"><span data-stu-id="64441-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="64441-130">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="64441-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="64441-131">Türler</span><span class="sxs-lookup"><span data-stu-id="64441-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="64441-132">güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="64441-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="64441-133">fixed deyimi</span><span class="sxs-lookup"><span data-stu-id="64441-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="64441-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="64441-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
