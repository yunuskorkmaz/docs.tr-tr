---
title: İşaretçi dönüştürmeleri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 308d5e0646eeb94012dbe18d46d6d33f67dfeaf5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698371"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="873bc-102">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="873bc-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="873bc-103">Aşağıdaki tabloda önceden tanımlanmış örtük işaretçi dönüşümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="873bc-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="873bc-104">Örtük dönüştürmeler, yöntem çağırma ve atama deyimleri dahil olmak üzere birçok durumda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="873bc-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="873bc-105">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="873bc-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="873bc-106">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="873bc-106">From</span></span>|<span data-ttu-id="873bc-107">Bitiş</span><span class="sxs-lookup"><span data-stu-id="873bc-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="873bc-108">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="873bc-108">Any pointer type</span></span>|<span data-ttu-id="873bc-109">Kağıt</span><span class="sxs-lookup"><span data-stu-id="873bc-109">void\*</span></span>|  
|<span data-ttu-id="873bc-110">{1&gt;null&lt;1}</span><span class="sxs-lookup"><span data-stu-id="873bc-110">null</span></span>|<span data-ttu-id="873bc-111">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="873bc-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="873bc-112">Açık işaretçi dönüştürmesi, bir atama ifadesi kullanarak örtük dönüştürme olmayan dönüştürmeler gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="873bc-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="873bc-113">Aşağıdaki tabloda bu dönüşümler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="873bc-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="873bc-114">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="873bc-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="873bc-115">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="873bc-115">From</span></span>|<span data-ttu-id="873bc-116">Bitiş</span><span class="sxs-lookup"><span data-stu-id="873bc-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="873bc-117">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="873bc-117">Any pointer type</span></span>|<span data-ttu-id="873bc-118">Diğer herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="873bc-118">Any other pointer type</span></span>|  
|<span data-ttu-id="873bc-119">SByte, Byte, Short, ushort, int, uint, Long veya ulong</span><span class="sxs-lookup"><span data-stu-id="873bc-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="873bc-120">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="873bc-120">Any pointer type</span></span>|  
|<span data-ttu-id="873bc-121">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="873bc-121">Any pointer type</span></span>|<span data-ttu-id="873bc-122">SByte, Byte, Short, ushort, int, uint, Long veya ulong</span><span class="sxs-lookup"><span data-stu-id="873bc-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="873bc-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="873bc-123">Example</span></span>  
 <span data-ttu-id="873bc-124">Aşağıdaki örnekte, `int` bir işaretçi `byte`işaretçisine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="873bc-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="873bc-125">İşaretçinin, değişkenin en düşük adresli baytını işaret ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="873bc-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="873bc-126">Sonucu büyük ölçüde artırdığınızda, `int` boyutuna kadar (4 bayt), değişkenin kalan baytlarını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="873bc-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="873bc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="873bc-127">See also</span></span>

- [<span data-ttu-id="873bc-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="873bc-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="873bc-129">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="873bc-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="873bc-130">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="873bc-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="873bc-131">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="873bc-131">Value types</span></span>](../../language-reference/keywords/value-types.md)
- [<span data-ttu-id="873bc-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="873bc-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="873bc-133">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="873bc-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="873bc-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="873bc-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
