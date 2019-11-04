---
title: İşaretçi dönüştürmeleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: b0a517eacc505376c9502e9d095c7aac0cd54555
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417528"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="b2483-102">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b2483-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="b2483-103">Aşağıdaki tabloda önceden tanımlanmış örtük işaretçi dönüşümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2483-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="b2483-104">Örtük dönüştürmeler, yöntem çağırma ve atama deyimleri dahil olmak üzere birçok durumda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="b2483-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="b2483-105">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b2483-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="b2483-106">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="b2483-106">From</span></span>|<span data-ttu-id="b2483-107">Bitiş</span><span class="sxs-lookup"><span data-stu-id="b2483-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b2483-108">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="b2483-108">Any pointer type</span></span>|<span data-ttu-id="b2483-109">Kağıt</span><span class="sxs-lookup"><span data-stu-id="b2483-109">void\*</span></span>|  
|<span data-ttu-id="b2483-110">null</span><span class="sxs-lookup"><span data-stu-id="b2483-110">null</span></span>|<span data-ttu-id="b2483-111">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="b2483-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="b2483-112">Açık işaretçi dönüştürmesi, bir atama ifadesi kullanarak örtük dönüştürme olmayan dönüştürmeler gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2483-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="b2483-113">Aşağıdaki tabloda bu dönüşümler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2483-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="b2483-114">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b2483-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="b2483-115">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="b2483-115">From</span></span>|<span data-ttu-id="b2483-116">Bitiş</span><span class="sxs-lookup"><span data-stu-id="b2483-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b2483-117">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="b2483-117">Any pointer type</span></span>|<span data-ttu-id="b2483-118">Diğer herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="b2483-118">Any other pointer type</span></span>|  
|<span data-ttu-id="b2483-119">SByte, Byte, Short, ushort, int, uint, Long veya ulong</span><span class="sxs-lookup"><span data-stu-id="b2483-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="b2483-120">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="b2483-120">Any pointer type</span></span>|  
|<span data-ttu-id="b2483-121">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="b2483-121">Any pointer type</span></span>|<span data-ttu-id="b2483-122">SByte, Byte, Short, ushort, int, uint, Long veya ulong</span><span class="sxs-lookup"><span data-stu-id="b2483-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b2483-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2483-123">Example</span></span>  
 <span data-ttu-id="b2483-124">Aşağıdaki örnekte, `int` bir işaretçi `byte`işaretçisine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="b2483-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="b2483-125">İşaretçinin, değişkenin en düşük adresli baytını işaret ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b2483-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="b2483-126">Sonucu büyük ölçüde artırdığınızda, `int` boyutuna kadar (4 bayt), değişkenin kalan baytlarını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2483-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b2483-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2483-127">See also</span></span>

- [<span data-ttu-id="b2483-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b2483-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b2483-129">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="b2483-129">Pointer types</span></span>](./pointer-types.md)
- [<span data-ttu-id="b2483-130">Türler</span><span class="sxs-lookup"><span data-stu-id="b2483-130">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="b2483-131">unsafe</span><span class="sxs-lookup"><span data-stu-id="b2483-131">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="b2483-132">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="b2483-132">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="b2483-133">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b2483-133">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
