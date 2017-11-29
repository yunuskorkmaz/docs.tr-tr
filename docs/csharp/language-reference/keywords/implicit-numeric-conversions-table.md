---
title: "Örtük Sayısal Dönüşümler Tablosu (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6b1705dca357fd2a155fc1ea9c7fe0f65bad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="52cb8-102">Örtük Sayısal Dönüşümler Tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="52cb8-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="52cb8-103">Aşağıdaki tabloda önceden tanımlanmış örtük sayısal dönüşümler gösterir.</span><span class="sxs-lookup"><span data-stu-id="52cb8-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="52cb8-104">Örtük dönüşümler yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="52cb8-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="52cb8-105">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="52cb8-105">From</span></span>|<span data-ttu-id="52cb8-106">Bitiş</span><span class="sxs-lookup"><span data-stu-id="52cb8-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="52cb8-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="52cb8-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="52cb8-108">`short`, `int`, `long`, `float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="52cb8-109">bayt</span><span class="sxs-lookup"><span data-stu-id="52cb8-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="52cb8-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="52cb8-111">kısa</span><span class="sxs-lookup"><span data-stu-id="52cb8-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="52cb8-112">`int`, `long`, `float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="52cb8-113">ushort</span><span class="sxs-lookup"><span data-stu-id="52cb8-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="52cb8-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="52cb8-115">int</span><span class="sxs-lookup"><span data-stu-id="52cb8-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="52cb8-116">`long`, `float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="52cb8-117">uint</span><span class="sxs-lookup"><span data-stu-id="52cb8-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="52cb8-118">`long`, `ulong`, `float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="52cb8-119">uzun</span><span class="sxs-lookup"><span data-stu-id="52cb8-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="52cb8-120">`float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="52cb8-121">char</span><span class="sxs-lookup"><span data-stu-id="52cb8-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="52cb8-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="52cb8-123">kayan nokta</span><span class="sxs-lookup"><span data-stu-id="52cb8-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="52cb8-124">ulong</span><span class="sxs-lookup"><span data-stu-id="52cb8-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="52cb8-125">`float`, `double`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="52cb8-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52cb8-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52cb8-126">Remarks</span></span>  
  
-   <span data-ttu-id="52cb8-127">Dönüşümleri içinde duyarlık ancak değil büyüklük kaybedilebilir `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.</span><span class="sxs-lookup"><span data-stu-id="52cb8-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="52cb8-128">Hiçbir örtük dönüşümler vardır `char` türü.</span><span class="sxs-lookup"><span data-stu-id="52cb8-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="52cb8-129">Kayan nokta türleri arasında örtük hiçbir dönüştürme vardır ve `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="52cb8-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="52cb8-130">Sabit bir ifade türü `int` dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, sağlanan Hedef aralık içinde sabit ifade değeri yazın.</span><span class="sxs-lookup"><span data-stu-id="52cb8-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="52cb8-131">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="52cb8-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="52cb8-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52cb8-132">See Also</span></span>  
 [<span data-ttu-id="52cb8-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="52cb8-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="52cb8-134">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="52cb8-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="52cb8-135">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="52cb8-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="52cb8-136">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="52cb8-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="52cb8-137">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="52cb8-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="52cb8-138">Atama ve tür dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="52cb8-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
