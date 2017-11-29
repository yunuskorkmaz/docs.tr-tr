---
title: "Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b05d77df28b560b9236e467a914229c0fa9ae7e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="81461-102">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="81461-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="81461-103">Çoğu veri türleri, yönetilen ve yönetilmeyen bellekte ortak bir gösterimi olan ve birlikte çalışma sıralayıcı tarafından özel işlem gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="81461-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="81461-104">Bu tür adlı *blittable türleri* arasında geçirildiğinde bunlar dönüştürme gerektirmediği için yönetilen ve yönetilmeyen kodu.</span><span class="sxs-lookup"><span data-stu-id="81461-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="81461-105">Platformundan döndürülen yapıları çağırma çağrıları blittable türleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="81461-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="81461-106">Platform çağırma blittable olmayan yapıları dönüş türleri olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="81461-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="81461-107">Aşağıdaki türleri <xref:System> ad alanı blittable türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="81461-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
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
  
 <span data-ttu-id="81461-108">Aşağıdaki karmaşık türler de blittable türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="81461-108">The following complex types are also blittable types:</span></span>  
  
-   <span data-ttu-id="81461-109">Blittable türleri dizisi gibi tek boyutlu dizi.</span><span class="sxs-lookup"><span data-stu-id="81461-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="81461-110">Ancak, bir değişken dizisini blittable türleri içeren bir tür kendisini değil blok halinde kopyalanabilir.</span><span class="sxs-lookup"><span data-stu-id="81461-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
-   <span data-ttu-id="81461-111">Yalnızca blittable türleri (ve biçimlendirilmiş türleri olarak sıralanmış varsa sınıfları) içeren biçimlendirilmiş değer türleri.</span><span class="sxs-lookup"><span data-stu-id="81461-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="81461-112">Biçimlendirilmiş değer türleri hakkında daha fazla bilgi için bkz: [değer türleri için varsayılan hazırlama](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a).</span><span class="sxs-lookup"><span data-stu-id="81461-112">For more information about formatted value types, see [Default Marshaling for Value Types](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a).</span></span>  
  
 <span data-ttu-id="81461-113">Nesne başvuruları blittable değil.</span><span class="sxs-lookup"><span data-stu-id="81461-113">Object references are not blittable.</span></span> <span data-ttu-id="81461-114">Bu başvurular blittable tek başına nesneler dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="81461-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="81461-115">Örneğin, blittable olan bir yapı tanımlayabilirsiniz, ancak bu yapıların başvurularını dizisini içeren bir blittable türü tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="81461-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="81461-116">Blok halinde kopyalanabilir türler yalnızca blittable üyeleri içeren sınıflar ve dizi bir iyileştirme olan [sabitlenmiş](../../../docs/framework/interop/copying-and-pinning.md) sıralama sırasında yerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="81461-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](../../../docs/framework/interop/copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="81461-117">Bu tür çağıran ve çağrılan aynı grupta olduğunda olarak In/Out parametreleri sıralanması görünebilir.</span><span class="sxs-lookup"><span data-stu-id="81461-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="81461-118">Ancak, bu tür gerçekte olduğu gibi parametreleri sıralanmış ve uygulamalısınız <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> bağımsız değişkeni olarak bir giriş/çıkış parametresi hazırlamak istiyorsanız öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="81461-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="81461-119">Bazı yönetilen veri türleri farklı gösterimi yönetilmeyen bir ortamda gerektirir.</span><span class="sxs-lookup"><span data-stu-id="81461-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="81461-120">Bu blittable olmayan veri türleri sıralanabilir bir forma dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="81461-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="81461-121">Örneğin, yönetilen dizeler kopyalanamaz türler şunlardır: çünkü bunlar sıralanabilir önce dize nesnelerini dönüştürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="81461-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="81461-122">Aşağıdaki tabloda blittable olmayan türlerinden listeler <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="81461-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="81461-123">[Temsilciler](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2), bir statik yöntem ya da bir sınıf örneği veri yapılarını olduğu olan ayrıca kopyalanamaz.</span><span class="sxs-lookup"><span data-stu-id="81461-123">[Delegates](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="81461-124">Örnekteki türü</span><span class="sxs-lookup"><span data-stu-id="81461-124">Non-blittable type</span></span>|<span data-ttu-id="81461-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81461-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="81461-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="81461-126">System.Array</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="81461-127">Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="81461-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="81461-128">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="81461-128">System.Boolean</span></span>](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|<span data-ttu-id="81461-129">1, 2 veya 4-bayt değeri ile dönüştürür `true` 1 veya -1 olarak.</span><span class="sxs-lookup"><span data-stu-id="81461-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|[<span data-ttu-id="81461-130">System.Char</span><span class="sxs-lookup"><span data-stu-id="81461-130">System.Char</span></span>](http://msdn.microsoft.com/en-us/cecc87c1-075e-4cde-aa56-33d189f66feb)|<span data-ttu-id="81461-131">Unicode veya ANSI karakter türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="81461-131">Converts to a Unicode or ANSI character.</span></span>|  
|[<span data-ttu-id="81461-132">System.Class</span><span class="sxs-lookup"><span data-stu-id="81461-132">System.Class</span></span>](http://msdn.microsoft.com/en-us/fe334af5-0123-43d8-be84-26f6f023ddb6)|<span data-ttu-id="81461-133">Bir sınıf arabirimi dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="81461-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="81461-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="81461-134">System.Object</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)|<span data-ttu-id="81461-135">Bir değişken veya arabirim dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="81461-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="81461-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="81461-136">System.Mdarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="81461-137">Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="81461-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="81461-138">System.String</span><span class="sxs-lookup"><span data-stu-id="81461-138">System.String</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)|<span data-ttu-id="81461-139">BSTR veya null başvuru sonlandırma bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="81461-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|[<span data-ttu-id="81461-140">System.Valuetype</span><span class="sxs-lookup"><span data-stu-id="81461-140">System.Valuetype</span></span>](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a)|<span data-ttu-id="81461-141">Bir sabit bellek düzeni yapısıyla dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="81461-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="81461-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="81461-142">System.Szarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="81461-143">Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="81461-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="81461-144">Sınıf ve nesne türleri yalnızca COM birlikte çalışma tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="81461-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="81461-145">Karşılık gelen türlerin [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# ve C++, bkz: [sınıf kitaplığına genel bakış](../../../docs/standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81461-145">For corresponding types in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++, see the [Class Library Overview](../../../docs/standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81461-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81461-146">See Also</span></span>  
 [<span data-ttu-id="81461-147">Varsayılan hazırlama davranışı</span><span class="sxs-lookup"><span data-stu-id="81461-147">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)
