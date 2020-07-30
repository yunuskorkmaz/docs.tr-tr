---
title: İşaretçi dönüştürmeleri-C# Programlama Kılavuzu
description: İşaretçi dönüştürmeleri hakkında bilgi edinin. Örtülü ve açık işaretçi dönüştürmelerinde, kod örneklerine ve kullanılabilir ek kaynakları görüntülemenize bakın.
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: c39be5cb52964abbea5bc5636c6fa74d8411a331
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382093"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="98c35-104">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="98c35-104">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="98c35-105">Aşağıdaki tabloda önceden tanımlanmış örtük işaretçi dönüşümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="98c35-105">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="98c35-106">Örtük dönüştürmeler, yöntem çağırma ve atama deyimleri dahil olmak üzere birçok durumda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="98c35-106">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="98c35-107">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="98c35-107">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="98c35-108">Kaynak</span><span class="sxs-lookup"><span data-stu-id="98c35-108">From</span></span>|<span data-ttu-id="98c35-109">Amaç</span><span class="sxs-lookup"><span data-stu-id="98c35-109">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="98c35-110">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="98c35-110">Any pointer type</span></span>|<span data-ttu-id="98c35-111">Kağıt</span><span class="sxs-lookup"><span data-stu-id="98c35-111">void\*</span></span>|  
|<span data-ttu-id="98c35-112">null</span><span class="sxs-lookup"><span data-stu-id="98c35-112">null</span></span>|<span data-ttu-id="98c35-113">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="98c35-113">Any pointer type</span></span>|  
  
 <span data-ttu-id="98c35-114">Açık işaretçi dönüştürmesi, bir atama ifadesi kullanarak örtük dönüştürme olmayan dönüştürmeler gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98c35-114">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="98c35-115">Aşağıdaki tabloda bu dönüşümler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="98c35-115">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="98c35-116">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="98c35-116">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="98c35-117">Kaynak</span><span class="sxs-lookup"><span data-stu-id="98c35-117">From</span></span>|<span data-ttu-id="98c35-118">Amaç</span><span class="sxs-lookup"><span data-stu-id="98c35-118">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="98c35-119">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="98c35-119">Any pointer type</span></span>|<span data-ttu-id="98c35-120">Diğer herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="98c35-120">Any other pointer type</span></span>|  
|<span data-ttu-id="98c35-121">SByte, Byte, Short, ushort, int, uint, Long veya ulong</span><span class="sxs-lookup"><span data-stu-id="98c35-121">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="98c35-122">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="98c35-122">Any pointer type</span></span>|  
|<span data-ttu-id="98c35-123">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="98c35-123">Any pointer type</span></span>|<span data-ttu-id="98c35-124">SByte, Byte, Short, ushort, int, uint, Long veya ulong</span><span class="sxs-lookup"><span data-stu-id="98c35-124">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="98c35-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="98c35-125">Example</span></span>  
 <span data-ttu-id="98c35-126">Aşağıdaki örnekte, için bir işaretçisi `int` işaretçisine dönüştürülür `byte` .</span><span class="sxs-lookup"><span data-stu-id="98c35-126">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="98c35-127">İşaretçinin, değişkenin en düşük adresli baytını işaret ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="98c35-127">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="98c35-128">Sonucu büyük ölçüde arttırdığınızda `int` (4 bayt), değişkenin kalan baytlarını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98c35-128">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="98c35-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98c35-129">See also</span></span>

- [<span data-ttu-id="98c35-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98c35-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="98c35-131">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="98c35-131">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="98c35-132">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="98c35-132">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="98c35-133">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="98c35-133">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="98c35-134">olmayabilecek</span><span class="sxs-lookup"><span data-stu-id="98c35-134">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="98c35-135">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="98c35-135">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="98c35-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="98c35-136">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
