---
title: Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 739f0efdb50f8eba4875a42d5173f741b6ee94b3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051894"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="f6acd-102">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="f6acd-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="f6acd-103">Çoğu veri türü hem yönetilen hem de yönetilmeyen bellekte ortak bir gösterimine sahiptir ve birlikte çalışma sıralayıcısı tarafından özel işleme gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f6acd-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="f6acd-104">Bu türler, yönetilen ve yönetilmeyen kod arasında geçirildiklerinde dönüştürme gerektirmediğinden *blittable türler* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f6acd-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="f6acd-105">Platform çağırma çağrılarının döndürdüğü yapıların blittable tür olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="f6acd-106">Platform çağırma, dönüş türleri olarak blittable olmayan yapıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f6acd-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="f6acd-107"><xref:System> Ad alanından aşağıdaki türler blittable türleridir:</span><span class="sxs-lookup"><span data-stu-id="f6acd-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="f6acd-108">Aşağıdaki karmaşık türler de blittable türleridir:</span><span class="sxs-lookup"><span data-stu-id="f6acd-108">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="f6acd-109">Tamsayılar dizisi gibi blittable türlerin tek boyutlu dizileri.</span><span class="sxs-lookup"><span data-stu-id="f6acd-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="f6acd-110">Ancak, blittable türlerin değişken dizisini içeren bir tür kendi blittable değildir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
- <span data-ttu-id="f6acd-111">Yalnızca blittable türlerini içeren biçimlendirilen değer türleri (ve bunları biçimli türler olarak sıralanmış olmaları durumunda sınıflar).</span><span class="sxs-lookup"><span data-stu-id="f6acd-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="f6acd-112">Biçimlendirilen değer türleri hakkında daha fazla bilgi için bkz. [değer türleri Için varsayılan sıralama](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="f6acd-112">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="f6acd-113">Nesne başvuruları blittable değildir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-113">Object references are not blittable.</span></span> <span data-ttu-id="f6acd-114">Bu, kendileri tarafından blittable olan nesnelere başvuru dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="f6acd-115">Örneğin, blittable olan bir yapı tanımlayabilirsiniz, ancak bu yapılara başvuru dizisi içeren bir blittable Türü tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f6acd-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="f6acd-116">En iyi duruma getirme olarak, blittable türündeki diziler ve yalnızca blittable üyeleri içeren sınıflar sıralama [](copying-and-pinning.md) sırasında kopyalanabilir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="f6acd-117">Çağıran ve çağrılan aynı Apartment olduğunda bu türler ın/out parametreleri olarak sıralanabilen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="f6acd-118">Ancak, bu türler aslında parametrelerde olarak sıralanır ve bağımsız değişkeni bir ın/out parametresi <xref:System.Runtime.InteropServices.InAttribute> olarak <xref:System.Runtime.InteropServices.OutAttribute> sıralamak istiyorsanız ve özniteliklerini uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="f6acd-119">Bazı yönetilen veri türleri, yönetilmeyen bir ortamda farklı bir temsil gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="f6acd-120">Bu blittable olmayan veri türlerinin sıralanabilen bir forma dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="f6acd-121">Örneğin, yönetilen dizeler, sıralanmadan önce dize nesnelerine dönüştürülmesi gerektiğinden blittable olmayan türlerdir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="f6acd-122">Aşağıdaki tabloda, <xref:System> ad alanından blittable olmayan türler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="f6acd-123">Statik bir yönteme veya bir sınıf örneğine başvuran veri yapıları olan [Temsilciler](default-marshaling-behavior.md#default-marshaling-for-delegates)de blittable değildir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-123">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="f6acd-124">Blittable olmayan tür</span><span class="sxs-lookup"><span data-stu-id="f6acd-124">Non-blittable type</span></span>|<span data-ttu-id="f6acd-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6acd-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="f6acd-126">System. Array</span><span class="sxs-lookup"><span data-stu-id="f6acd-126">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="f6acd-127">C stili bir diziye veya `SAFEARRAY`öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="f6acd-128">[System. Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f6acd-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="f6acd-129">1, 2 veya 4 baytlık bir değere 1 veya-1 ile `true` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="f6acd-130">[System. Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f6acd-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="f6acd-131">Unicode veya ANSI karaktere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-131">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="f6acd-132">[System. Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f6acd-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="f6acd-133">Sınıf arabirimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="f6acd-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="f6acd-134">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="f6acd-135">Bir varyanta veya arabirime dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="f6acd-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="f6acd-136">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="f6acd-137">C stili bir diziye veya `SAFEARRAY`öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="f6acd-138">System. String</span><span class="sxs-lookup"><span data-stu-id="f6acd-138">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="f6acd-139">Null bir başvuruya veya BSTR 'ye bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="f6acd-140">[System. ValueType](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f6acd-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="f6acd-141">Sabit bellek düzenine sahip bir yapıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="f6acd-142">System. Szarray</span><span class="sxs-lookup"><span data-stu-id="f6acd-142">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="f6acd-143">C stili bir diziye veya `SAFEARRAY`öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6acd-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="f6acd-144">Sınıf ve nesne türleri yalnızca COM birlikte çalışma tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f6acd-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="f6acd-145">Visual Basic, C#ve C++içindeki karşılık gelen türler Için bkz. [sınıf kitaplığına genel bakış](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f6acd-145">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6acd-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6acd-146">See also</span></span>

- [<span data-ttu-id="f6acd-147">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="f6acd-147">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
