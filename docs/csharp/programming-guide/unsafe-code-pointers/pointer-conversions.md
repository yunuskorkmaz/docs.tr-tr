---
title: İşaretçi dönüşümleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 8fa1c1442d146c9d2fbdb2fa969b2e29d7ef765d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498313"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="5e504-102">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5e504-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="5e504-103">Aşağıdaki tablo, önceden tanımlanmış örtük işaretçi dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e504-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="5e504-104">Örtük dönüştürmeleri yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="5e504-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="5e504-105">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="5e504-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="5e504-106">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="5e504-106">From</span></span>|<span data-ttu-id="5e504-107">Bitiş</span><span class="sxs-lookup"><span data-stu-id="5e504-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="5e504-108">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="5e504-108">Any pointer type</span></span>|<span data-ttu-id="5e504-109">void \*</span><span class="sxs-lookup"><span data-stu-id="5e504-109">void\*</span></span>|  
|<span data-ttu-id="5e504-110">null</span><span class="sxs-lookup"><span data-stu-id="5e504-110">null</span></span>|<span data-ttu-id="5e504-111">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="5e504-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="5e504-112">Açık işaretçi dönüştürme dönüştürmeler, var olan herhangi bir örtük dönüştürmeyi atama ifadesini kullanarak gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e504-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="5e504-113">Aşağıdaki tabloda, bu dönüştürmeleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e504-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="5e504-114">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="5e504-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="5e504-115">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="5e504-115">From</span></span>|<span data-ttu-id="5e504-116">Bitiş</span><span class="sxs-lookup"><span data-stu-id="5e504-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="5e504-117">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="5e504-117">Any pointer type</span></span>|<span data-ttu-id="5e504-118">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="5e504-118">Any other pointer type</span></span>|  
|<span data-ttu-id="5e504-119">sbyte, byte, kısa, ushort, int, uint, long veya ulong</span><span class="sxs-lookup"><span data-stu-id="5e504-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="5e504-120">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="5e504-120">Any pointer type</span></span>|  
|<span data-ttu-id="5e504-121">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="5e504-121">Any pointer type</span></span>|<span data-ttu-id="5e504-122">sbyte, byte, kısa, ushort, int, uint, long veya ulong</span><span class="sxs-lookup"><span data-stu-id="5e504-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5e504-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e504-123">Example</span></span>  
 <span data-ttu-id="5e504-124">Aşağıdaki örnekte, bir işaretçi `int` işaretçisine dönüştürülür `byte`.</span><span class="sxs-lookup"><span data-stu-id="5e504-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="5e504-125">İşaretçiyi en düşük adresli baytına değişkenin işaret dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5e504-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="5e504-126">Ne zaman sırayla artırmanız boyutu en fazla sonuç `int` (4 bayt), kalan baytlar değişkenin görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e504-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5e504-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e504-127">See also</span></span>

- [<span data-ttu-id="5e504-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5e504-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5e504-129">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="5e504-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="5e504-130">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="5e504-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="5e504-131">Türler</span><span class="sxs-lookup"><span data-stu-id="5e504-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="5e504-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="5e504-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="5e504-133">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="5e504-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="5e504-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="5e504-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
