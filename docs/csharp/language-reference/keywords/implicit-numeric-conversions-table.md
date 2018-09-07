---
title: Örtük Sayısal Dönüşümler Tablosu (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 4bbc6086dc5fd3838ef9361762c3068ca44efd0e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047987"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="ec7e8-102">Örtük Sayısal Dönüşümler Tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ec7e8-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="ec7e8-103">Aşağıdaki tablo, önceden tanımlanmış örtük sayısal dönüşümler gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec7e8-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="ec7e8-104">Örtük dönüştürmeleri yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ec7e8-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="ec7e8-105">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="ec7e8-105">From</span></span>|<span data-ttu-id="ec7e8-106">Bitiş</span><span class="sxs-lookup"><span data-stu-id="ec7e8-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="ec7e8-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="ec7e8-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="ec7e8-108">`short`, `int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="ec7e8-109">byte</span><span class="sxs-lookup"><span data-stu-id="ec7e8-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="ec7e8-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="ec7e8-111">short</span><span class="sxs-lookup"><span data-stu-id="ec7e8-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="ec7e8-112">`int`, `long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="ec7e8-113">ushort</span><span class="sxs-lookup"><span data-stu-id="ec7e8-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="ec7e8-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="ec7e8-115">int</span><span class="sxs-lookup"><span data-stu-id="ec7e8-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="ec7e8-116">`long`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="ec7e8-117">uint</span><span class="sxs-lookup"><span data-stu-id="ec7e8-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="ec7e8-118">`long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="ec7e8-119">long</span><span class="sxs-lookup"><span data-stu-id="ec7e8-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="ec7e8-120">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="ec7e8-121">char</span><span class="sxs-lookup"><span data-stu-id="ec7e8-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="ec7e8-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="ec7e8-123">float</span><span class="sxs-lookup"><span data-stu-id="ec7e8-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="ec7e8-124">ulong</span><span class="sxs-lookup"><span data-stu-id="ec7e8-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="ec7e8-125">`float`, `double`, veya `decimal`</span><span class="sxs-lookup"><span data-stu-id="ec7e8-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec7e8-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec7e8-126">Remarks</span></span>  
  
-   <span data-ttu-id="ec7e8-127">Duyarlık ancak değil büyüklük kayıp dönüşümlerse içinde `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.</span><span class="sxs-lookup"><span data-stu-id="ec7e8-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="ec7e8-128">Herhangi bir örtük dönüştürme vardır `char` türü.</span><span class="sxs-lookup"><span data-stu-id="ec7e8-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="ec7e8-129">Kayan nokta türleri arasında örtük dönüştürme işlemi yok ve `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="ec7e8-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="ec7e8-130">Sabit bir ifade türü `int` dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, sağlanan hedef aralığı içinde sabit ifade değeri yazın.</span><span class="sxs-lookup"><span data-stu-id="ec7e8-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ec7e8-131">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="ec7e8-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ec7e8-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec7e8-132">See Also</span></span>  

- [<span data-ttu-id="ec7e8-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ec7e8-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ec7e8-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ec7e8-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ec7e8-135">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="ec7e8-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="ec7e8-136">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="ec7e8-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="ec7e8-137">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="ec7e8-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [<span data-ttu-id="ec7e8-138">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="ec7e8-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
