---
title: Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37b226cad9a34f1629d2972dacf8019adad54d7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115381"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="dfe14-102">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="dfe14-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="dfe14-103">Çoğu veri türleri, hem yönetilen hem de yönetilmeyen bellekte bir ortak gösterilmesi ve birlikte çalışma sıralayıcısı ile özel işlem gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="dfe14-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="dfe14-104">Bu tür adında *türlerse* arasında geçirildiğinde, dönüştürme gerektirmediği için yönetilen ve yönetilmeyen kod.</span><span class="sxs-lookup"><span data-stu-id="dfe14-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="dfe14-105">Platformdan iade yapıları çağırma çağrıları blok halinde kopyalanabilir türler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="dfe14-106">Platform çağırma dönüş türleri olarak kopyalanamaz yapıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="dfe14-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="dfe14-107">Aşağıdaki türlerini <xref:System> ad alanı blittable türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dfe14-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="dfe14-108">Aşağıdaki karmaşık türler, ayrıca blittable türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dfe14-108">The following complex types are also blittable types:</span></span>  
  
-   <span data-ttu-id="dfe14-109">Tamsayı dizisi gibi belirli bir türlerse tek boyutlu dizi.</span><span class="sxs-lookup"><span data-stu-id="dfe14-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="dfe14-110">Ancak blittable türleri değişken bir dizi içeren bir tür kendisini değil blok halinde kopyalanabilir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
-   <span data-ttu-id="dfe14-111">Biçimlendirilmiş değer türleri yalnızca bir blok halinde kopyalanabilir türler (ve biçimlendirilmiş türleri olarak sıralanmış, sınıflar) bulunur.</span><span class="sxs-lookup"><span data-stu-id="dfe14-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="dfe14-112">Biçimlendirilmiş değer türleri hakkında daha fazla bilgi için bkz: [değer türleri için varsayılan hazırlama](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="dfe14-112">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="dfe14-113">Nesne başvuruları blittable değil.</span><span class="sxs-lookup"><span data-stu-id="dfe14-113">Object references are not blittable.</span></span> <span data-ttu-id="dfe14-114">Bu blittable başlarına olan nesnelere yapılan başvuruların dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="dfe14-115">Örneğin, blittable bir yapısı tanımlayabilirsiniz, ancak bu yapıların yapılan başvuruların dizisi içeren bir blok halinde kopyalanabilir türü tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dfe14-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="dfe14-116">Bir iyileştirme blok halinde kopyalanabilir türler yalnızca blittable üyeleri içeren sınıflar ve dizilerdir [sabitlenmiş](../../../docs/framework/interop/copying-and-pinning.md) yerine sıralama sırasında kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](../../../docs/framework/interop/copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="dfe14-117">Bu türler, çağıran ve çağrılan aynı grupta olduğunda In/Out parametreleri sıralanması görünebilir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="dfe14-118">Ancak, bu tür parametreleri olduğu gibi gerçekten sıralanmış ve uygulamalısınız <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> bağımsız değişkeni olarak bir ın/Out parametresi hazırlamak istiyorsanız öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="dfe14-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="dfe14-119">Bazı yönetilen veri türleri, yönetilmeyen bir ortamda farklı bir gösterimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="dfe14-120">Bu blittable olmayan veri türlerini sıralanabilir bir biçime dönüştürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="dfe14-121">Örneğin, çünkü bunlar sıralanabilir önce dize nesnelerini dönüştürülmelidir yönetilen dizeler kopyalanamaz türler ' dir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="dfe14-122">Kopyalanamaz türleri aşağıdaki tabloda <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="dfe14-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="dfe14-123">[Temsilciler](default-marshaling-behavior.md#default-marshaling-for-delegates), statik bir yöntem veya bir sınıf örneğine başvuruda bulunan veri yapılarını hangilerinin ayrıca kopyalanamaz.</span><span class="sxs-lookup"><span data-stu-id="dfe14-123">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="dfe14-124">Örnekteki türü</span><span class="sxs-lookup"><span data-stu-id="dfe14-124">Non-blittable type</span></span>|<span data-ttu-id="dfe14-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfe14-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="dfe14-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="dfe14-126">System.Array</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="dfe14-127">Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="dfe14-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="dfe14-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dfe14-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="dfe14-129">1, 2 veya 4 baytlık değeriyle dönüştürür `true` 1 veya -1 olarak.</span><span class="sxs-lookup"><span data-stu-id="dfe14-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="dfe14-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dfe14-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="dfe14-131">Bir Unicode veya ANSI karakterine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dfe14-131">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="dfe14-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dfe14-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="dfe14-133">Sınıf arabirimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dfe14-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="dfe14-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="dfe14-134">System.Object</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)|<span data-ttu-id="dfe14-135">Bir değişken veya bir arabirim dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dfe14-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="dfe14-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="dfe14-136">System.Mdarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="dfe14-137">Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="dfe14-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="dfe14-138">System.String</span><span class="sxs-lookup"><span data-stu-id="dfe14-138">System.String</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)|<span data-ttu-id="dfe14-139">BSTR veya null başvuru sonlandıran bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dfe14-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="dfe14-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dfe14-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="dfe14-141">Sabit bellek düzeni ile bir yapıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dfe14-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="dfe14-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="dfe14-142">System.Szarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="dfe14-143">Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="dfe14-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="dfe14-144">Sınıf ve nesne türleri yalnızca COM birlikte çalışma tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="dfe14-145">Karşılık gelen türler için [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#ve C++ bkz [sınıf kitaplığına genel bakış](../../../docs/standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dfe14-145">For corresponding types in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++, see the [Class Library Overview](../../../docs/standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe14-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfe14-146">See also</span></span>

- [<span data-ttu-id="dfe14-147">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="dfe14-147">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)
