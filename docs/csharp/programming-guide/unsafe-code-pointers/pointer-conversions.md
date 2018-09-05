---
title: İşaretçi Dönüşümleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: db809fa9e086351184adcac43d67f53e9456894c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554141"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="886ee-102">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="886ee-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="886ee-103">Aşağıdaki tablo, önceden tanımlanmış örtük işaretçi dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="886ee-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="886ee-104">Örtük dönüştürmeleri yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="886ee-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="886ee-105">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="886ee-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="886ee-106">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="886ee-106">From</span></span>|<span data-ttu-id="886ee-107">Bitiş</span><span class="sxs-lookup"><span data-stu-id="886ee-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="886ee-108">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="886ee-108">Any pointer type</span></span>|<span data-ttu-id="886ee-109">void \*</span><span class="sxs-lookup"><span data-stu-id="886ee-109">void\*</span></span>|  
|<span data-ttu-id="886ee-110">null</span><span class="sxs-lookup"><span data-stu-id="886ee-110">null</span></span>|<span data-ttu-id="886ee-111">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="886ee-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="886ee-112">Açık işaretçi dönüştürme dönüştürmeler, var olan herhangi bir örtük dönüştürmeyi atama ifadesini kullanarak gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="886ee-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="886ee-113">Aşağıdaki tabloda, bu dönüştürmeleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="886ee-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="886ee-114">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="886ee-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="886ee-115">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="886ee-115">From</span></span>|<span data-ttu-id="886ee-116">Bitiş</span><span class="sxs-lookup"><span data-stu-id="886ee-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="886ee-117">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="886ee-117">Any pointer type</span></span>|<span data-ttu-id="886ee-118">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="886ee-118">Any other pointer type</span></span>|  
|<span data-ttu-id="886ee-119">sbyte, byte, kısa, ushort, int, uint, long veya ulong</span><span class="sxs-lookup"><span data-stu-id="886ee-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="886ee-120">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="886ee-120">Any pointer type</span></span>|  
|<span data-ttu-id="886ee-121">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="886ee-121">Any pointer type</span></span>|<span data-ttu-id="886ee-122">sbyte, byte, kısa, ushort, int, uint, long veya ulong</span><span class="sxs-lookup"><span data-stu-id="886ee-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="886ee-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="886ee-123">Example</span></span>  
 <span data-ttu-id="886ee-124">Aşağıdaki örnekte, bir işaretçi `int` işaretçisine dönüştürülür `byte`.</span><span class="sxs-lookup"><span data-stu-id="886ee-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="886ee-125">İşaretçiyi en düşük adresli baytına değişkenin işaret dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="886ee-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="886ee-126">Ne zaman sırayla artırmanız boyutu en fazla sonuç `int` (4 bayt), kalan baytlar değişkenin görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="886ee-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="886ee-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="886ee-127">See Also</span></span>

- [<span data-ttu-id="886ee-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="886ee-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="886ee-129">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="886ee-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="886ee-130">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="886ee-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="886ee-131">Türler</span><span class="sxs-lookup"><span data-stu-id="886ee-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="886ee-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="886ee-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="886ee-133">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="886ee-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="886ee-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="886ee-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
