---
title: İşaretçi Dönüşümleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: e0c3a409d76468a6e214a96e8bb326a9d906fe18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322698"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="79104-102">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="79104-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="79104-103">Aşağıdaki tabloda önceden tanımlanmış örtük işaretçi dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="79104-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="79104-104">Örtük dönüşümler yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="79104-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="79104-105">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="79104-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="79104-106">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="79104-106">From</span></span>|<span data-ttu-id="79104-107">Bitiş</span><span class="sxs-lookup"><span data-stu-id="79104-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="79104-108">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="79104-108">Any pointer type</span></span>|<span data-ttu-id="79104-109">void \*</span><span class="sxs-lookup"><span data-stu-id="79104-109">void\*</span></span>|  
|<span data-ttu-id="79104-110">null</span><span class="sxs-lookup"><span data-stu-id="79104-110">null</span></span>|<span data-ttu-id="79104-111">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="79104-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="79104-112">Açık işaretçi dönüştürme var olduğu örtük dönüştürme, bir cast ifadesi kullanarak dönüşümlerini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79104-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="79104-113">Aşağıdaki tabloda bu dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="79104-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="79104-114">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="79104-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="79104-115">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="79104-115">From</span></span>|<span data-ttu-id="79104-116">Bitiş</span><span class="sxs-lookup"><span data-stu-id="79104-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="79104-117">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="79104-117">Any pointer type</span></span>|<span data-ttu-id="79104-118">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="79104-118">Any other pointer type</span></span>|  
|<span data-ttu-id="79104-119">sbyte, bayt, short, ushort, int, uint, uzun veya ulong</span><span class="sxs-lookup"><span data-stu-id="79104-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="79104-120">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="79104-120">Any pointer type</span></span>|  
|<span data-ttu-id="79104-121">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="79104-121">Any pointer type</span></span>|<span data-ttu-id="79104-122">sbyte, bayt, short, ushort, int, uint, uzun veya ulong</span><span class="sxs-lookup"><span data-stu-id="79104-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="79104-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="79104-123">Example</span></span>  
 <span data-ttu-id="79104-124">Aşağıdaki örnekte, bir işaretçi `int` gösteren bir işaretçi dönüştürülür `byte`.</span><span class="sxs-lookup"><span data-stu-id="79104-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="79104-125">İşaretçinin en düşük adresli bayta değişkenin işaret dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="79104-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="79104-126">Ne zaman, sırayla Artır boyutu kadar sonuç `int` (4 bayt), değişkenin kalan bayt sayısı görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79104-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="79104-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79104-127">See Also</span></span>  
 [<span data-ttu-id="79104-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="79104-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="79104-129">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="79104-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="79104-130">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="79104-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="79104-131">Türler</span><span class="sxs-lookup"><span data-stu-id="79104-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="79104-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="79104-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="79104-133">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="79104-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="79104-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="79104-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
