---
title: İşaretçi dönüştürmeleri-C# Programlama Kılavuzu
description: İşaretçi dönüştürmeleri hakkında bilgi edinin. Örtülü ve açık işaretçi dönüştürmelerinde, kod örneklerine ve kullanılabilir ek kaynakları görüntülemenize bakın.
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 7a37c4e9f6333c00c7842df0fdaf353df516974d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205080"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="67ee4-104">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="67ee4-104">Pointer Conversions (C# Programming Guide)</span></span>

<span data-ttu-id="67ee4-105">Aşağıdaki tabloda önceden tanımlanmış örtük işaretçi dönüşümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67ee4-105">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="67ee4-106">Örtük dönüştürmeler, yöntem çağırma ve atama deyimleri dahil olmak üzere birçok durumda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="67ee4-106">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="67ee4-107">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="67ee4-107">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="67ee4-108">Kaynak</span><span class="sxs-lookup"><span data-stu-id="67ee4-108">From</span></span>|<span data-ttu-id="67ee4-109">Amaç</span><span class="sxs-lookup"><span data-stu-id="67ee4-109">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="67ee4-110">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="67ee4-110">Any pointer type</span></span>|<span data-ttu-id="67ee4-111">Kağıt</span><span class="sxs-lookup"><span data-stu-id="67ee4-111">void\*</span></span>|  
|<span data-ttu-id="67ee4-112">null</span><span class="sxs-lookup"><span data-stu-id="67ee4-112">null</span></span>|<span data-ttu-id="67ee4-113">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="67ee4-113">Any pointer type</span></span>|  
  
 <span data-ttu-id="67ee4-114">Açık işaretçi dönüştürmesi, bir atama ifadesi kullanarak örtük dönüştürme olmayan dönüştürmeler gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67ee4-114">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="67ee4-115">Aşağıdaki tabloda bu dönüşümler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67ee4-115">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="67ee4-116">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="67ee4-116">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="67ee4-117">Kaynak</span><span class="sxs-lookup"><span data-stu-id="67ee4-117">From</span></span>|<span data-ttu-id="67ee4-118">Amaç</span><span class="sxs-lookup"><span data-stu-id="67ee4-118">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="67ee4-119">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="67ee4-119">Any pointer type</span></span>|<span data-ttu-id="67ee4-120">Diğer herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="67ee4-120">Any other pointer type</span></span>|  
|<span data-ttu-id="67ee4-121">SByte, Byte, Short, ushort, int, uint, Long veya ulong</span><span class="sxs-lookup"><span data-stu-id="67ee4-121">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="67ee4-122">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="67ee4-122">Any pointer type</span></span>|  
|<span data-ttu-id="67ee4-123">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="67ee4-123">Any pointer type</span></span>|<span data-ttu-id="67ee4-124">SByte, Byte, Short, ushort, int, uint, Long veya ulong</span><span class="sxs-lookup"><span data-stu-id="67ee4-124">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="67ee4-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="67ee4-125">Example</span></span>  

 <span data-ttu-id="67ee4-126">Aşağıdaki örnekte, için bir işaretçisi `int` işaretçisine dönüştürülür `byte` .</span><span class="sxs-lookup"><span data-stu-id="67ee4-126">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="67ee4-127">İşaretçinin, değişkenin en düşük adresli baytını işaret ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="67ee4-127">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="67ee4-128">Sonucu büyük ölçüde arttırdığınızda `int` (4 bayt), değişkenin kalan baytlarını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67ee4-128">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="67ee4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67ee4-129">See also</span></span>

- [<span data-ttu-id="67ee4-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="67ee4-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="67ee4-131">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="67ee4-131">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="67ee4-132">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="67ee4-132">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="67ee4-133">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="67ee4-133">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="67ee4-134">olmayabilecek</span><span class="sxs-lookup"><span data-stu-id="67ee4-134">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="67ee4-135">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="67ee4-135">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="67ee4-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="67ee4-136">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
