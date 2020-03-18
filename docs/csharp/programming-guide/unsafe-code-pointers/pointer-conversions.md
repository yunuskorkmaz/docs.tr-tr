---
title: İşaretçi Dönüşümleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745368"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="e2d52-102">İşaretçi Dönüşümleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e2d52-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="e2d52-103">Aşağıdaki tablo, önceden tanımlanmış örtük işaretçi dönüşümlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2d52-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="e2d52-104">Örtülü dönüşümler, yöntem arama ve atama deyimleri de dahil olmak üzere birçok durumda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="e2d52-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="e2d52-105">Örtük işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="e2d52-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="e2d52-106">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="e2d52-106">From</span></span>|<span data-ttu-id="e2d52-107">Alıcı</span><span class="sxs-lookup"><span data-stu-id="e2d52-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="e2d52-108">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="e2d52-108">Any pointer type</span></span>|<span data-ttu-id="e2d52-109">geçersiz\*</span><span class="sxs-lookup"><span data-stu-id="e2d52-109">void\*</span></span>|  
|<span data-ttu-id="e2d52-110">null</span><span class="sxs-lookup"><span data-stu-id="e2d52-110">null</span></span>|<span data-ttu-id="e2d52-111">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="e2d52-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="e2d52-112">Açık işaretçi dönüştürme, bir döküm ifadesi kullanılarak, örtülü dönüştürme bulunmayan dönüşümleri gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2d52-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="e2d52-113">Aşağıdaki tabloda bu dönüşümler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e2d52-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="e2d52-114">Açık işaretçi dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="e2d52-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="e2d52-115">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="e2d52-115">From</span></span>|<span data-ttu-id="e2d52-116">Alıcı</span><span class="sxs-lookup"><span data-stu-id="e2d52-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="e2d52-117">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="e2d52-117">Any pointer type</span></span>|<span data-ttu-id="e2d52-118">Diğer işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="e2d52-118">Any other pointer type</span></span>|  
|<span data-ttu-id="e2d52-119">bayt, bayt, kısa, ushort, int, uint, uzun veya ulong</span><span class="sxs-lookup"><span data-stu-id="e2d52-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="e2d52-120">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="e2d52-120">Any pointer type</span></span>|  
|<span data-ttu-id="e2d52-121">Herhangi bir işaretçi türü</span><span class="sxs-lookup"><span data-stu-id="e2d52-121">Any pointer type</span></span>|<span data-ttu-id="e2d52-122">bayt, bayt, kısa, ushort, int, uint, uzun veya ulong</span><span class="sxs-lookup"><span data-stu-id="e2d52-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e2d52-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2d52-123">Example</span></span>  
 <span data-ttu-id="e2d52-124">Aşağıdaki örnekte, işaretçi `int` için bir işaretçi `byte`için bir işaretçi dönüştürülür .</span><span class="sxs-lookup"><span data-stu-id="e2d52-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="e2d52-125">İşaretçinin değişkenin en düşük adresli baytını işaret ettiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e2d52-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="e2d52-126">Sonucu art arda `int` ,(4 bayt) boyutuna kadar artımladiğinizde, değişkenin kalan baytlarını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2d52-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e2d52-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2d52-127">See also</span></span>

- [<span data-ttu-id="e2d52-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e2d52-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e2d52-129">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="e2d52-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="e2d52-130">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="e2d52-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="e2d52-131">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="e2d52-131">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="e2d52-132">Güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="e2d52-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="e2d52-133">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="e2d52-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="e2d52-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="e2d52-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
