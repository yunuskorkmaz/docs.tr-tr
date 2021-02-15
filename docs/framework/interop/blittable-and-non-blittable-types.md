---
title: Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler
description: Blittable ve blittable olmayan türler hakkında bilgi edinin. Blittable veri türleri genellikle yönetilen ve yönetilmeyen bellekte temsil edilir ve özel işleme gerektirmez.
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: c9168bd245e10232a798b3e6f3b9448b24996a77
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436129"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="2e8c5-104">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="2e8c5-104">Blittable and Non-Blittable Types</span></span>

<span data-ttu-id="2e8c5-105">Çoğu veri türü hem yönetilen hem de yönetilmeyen bellekte ortak bir gösterimine sahiptir ve birlikte çalışma sıralayıcısı tarafından özel işleme gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-105">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="2e8c5-106">Bu türler, yönetilen ve yönetilmeyen kod arasında geçirildiklerinde dönüştürme gerektirmediğinden *blittable türler* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-106">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="2e8c5-107">Platform çağırma çağrılarının döndürdüğü yapıların blittable tür olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-107">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="2e8c5-108">Platform çağırma, dönüş türleri olarak blittable olmayan yapıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-108">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="2e8c5-109">Ad alanından aşağıdaki türler <xref:System> blittable türleridir:</span><span class="sxs-lookup"><span data-stu-id="2e8c5-109">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
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
  
 <span data-ttu-id="2e8c5-110">Aşağıdaki karmaşık türler de blittable türleridir:</span><span class="sxs-lookup"><span data-stu-id="2e8c5-110">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="2e8c5-111">Bir tamsayılar dizisi gibi, blittable basit türlerin tek boyutlu dizileri.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-111">One-dimensional arrays of blittable primitive types, such as an array of integers.</span></span> <span data-ttu-id="2e8c5-112">Ancak, blittable türlerin değişken dizisini içeren bir tür kendi blittable değildir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-112">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>
  
- <span data-ttu-id="2e8c5-113">Yalnızca blittable türlerini içeren biçimlendirilen değer türleri (ve bunları biçimli türler olarak sıralanmış olmaları durumunda sınıflar).</span><span class="sxs-lookup"><span data-stu-id="2e8c5-113">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="2e8c5-114">Biçimlendirilen değer türleri hakkında daha fazla bilgi için bkz. [değer türleri Için varsayılan sıralama](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="2e8c5-114">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="2e8c5-115">Nesne başvuruları blittable değildir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-115">Object references are not blittable.</span></span> <span data-ttu-id="2e8c5-116">Bu, kendileri tarafından blittable olan nesnelere başvuru dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-116">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="2e8c5-117">Örneğin, blittable olan bir yapı tanımlayabilirsiniz, ancak bu yapılara başvuru dizisi içeren bir blittable Türü tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-117">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="2e8c5-118">En iyi duruma getirme olarak, blittable temel türleri ve yalnızca blittable üyeleri içeren sınıfların dizileri, sıralama sırasında kopyalanmaları yerine [sabitlenmiştir](copying-and-pinning.md) .</span><span class="sxs-lookup"><span data-stu-id="2e8c5-118">As an optimization, arrays of blittable primitive types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="2e8c5-119">Çağıran ve çağrılan aynı Apartment olduğunda bu türler ın/out parametreleri olarak sıralanabilen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-119">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="2e8c5-120">Ancak, bu türler aslında parametrelerde olarak sıralanır ve <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> bağımsız değişkeni bir ın/out parametresi olarak sıralamak istiyorsanız ve özniteliklerini uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-120">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>
  
 <span data-ttu-id="2e8c5-121">Bazı yönetilen veri türleri, yönetilmeyen bir ortamda farklı bir temsil gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-121">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="2e8c5-122">Bu blittable olmayan veri türlerinin sıralanabilen bir forma dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-122">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="2e8c5-123">Örneğin, yönetilen dizeler, sıralanmadan önce dize nesnelerine dönüştürülmesi gerektiğinden blittable olmayan türlerdir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-123">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="2e8c5-124">Aşağıdaki tabloda, ad alanından blittable olmayan türler listelenmektedir <xref:System> .</span><span class="sxs-lookup"><span data-stu-id="2e8c5-124">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="2e8c5-125">Statik bir yönteme veya bir sınıf örneğine başvuran veri yapıları olan [Temsilciler](default-marshaling-behavior.md#default-marshaling-for-delegates)de blittable değildir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-125">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="2e8c5-126">Blittable olmayan tür</span><span class="sxs-lookup"><span data-stu-id="2e8c5-126">Non-blittable type</span></span>|<span data-ttu-id="2e8c5-127">Description</span><span class="sxs-lookup"><span data-stu-id="2e8c5-127">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="2e8c5-128">System. Array</span><span class="sxs-lookup"><span data-stu-id="2e8c5-128">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="2e8c5-129">C stili bir diziye veya öğesine dönüştürür `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="2e8c5-129">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="2e8c5-130">[System. Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e8c5-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="2e8c5-131">1, 2 veya 4 baytlık bir değere `true` 1 veya-1 ile dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-131">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="2e8c5-132">[System. Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e8c5-132">[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="2e8c5-133">Unicode veya ANSI karaktere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-133">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="2e8c5-134">[System. Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e8c5-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="2e8c5-135">Sınıf arabirimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-135">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="2e8c5-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="2e8c5-136">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="2e8c5-137">Bir varyanta veya arabirime dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-137">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="2e8c5-138">System. Mdarray</span><span class="sxs-lookup"><span data-stu-id="2e8c5-138">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="2e8c5-139">C stili bir diziye veya öğesine dönüştürür `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="2e8c5-139">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="2e8c5-140">System. String</span><span class="sxs-lookup"><span data-stu-id="2e8c5-140">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="2e8c5-141">Null bir başvuruya veya BSTR 'ye bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-141">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="2e8c5-142">[System. ValueType](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e8c5-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="2e8c5-143">Sabit bellek düzenine sahip bir yapıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-143">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="2e8c5-144">System. Szarray</span><span class="sxs-lookup"><span data-stu-id="2e8c5-144">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="2e8c5-145">C stili bir diziye veya öğesine dönüştürür `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="2e8c5-145">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="2e8c5-146">Sınıf ve nesne türleri yalnızca COM birlikte çalışma tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-146">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="2e8c5-147">Visual Basic, C# ve C++ ' daki ilgili türler için bkz. [sınıf kitaplığına genel bakış](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e8c5-147">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8c5-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e8c5-148">See also</span></span>

- [<span data-ttu-id="2e8c5-149">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="2e8c5-149">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
