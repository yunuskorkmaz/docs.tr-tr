---
title: Varsayılan Hazırlama Davranışı
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83bb8b0305e47ca7b354db03c7a9a3dd02f62d41
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028077"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="e7010-102">Varsayılan Hazırlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="e7010-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="e7010-103">Birlikte çalışma hazırlama kurallarında yönetilen ve yönetilmeyen bellek arasında geçerken yöntem parametreleri ile ilişkili verileri nasıl davranacağını bu dikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="e7010-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="e7010-104">Bu yerleşik kurallar bir Aranan kendisine geçirilen verileri değiştirebilir ve bu değişiklikleri çağırana dönün ve altında Sıralayıcı koşulda performans iyileştirmelerini sağlar hazırlama gibi etkinlikler veri türü dönüşümleri olarak denetler.</span><span class="sxs-lookup"><span data-stu-id="e7010-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="e7010-105">Bu bölüm, hizmet hazırlama birlikte çalışabilirliği varsayılan davranış özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7010-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="e7010-106">Diziler, Boolean türleri, karakter türleri, temsilciler, sınıflar, nesneler, dizeleri ve yapıları hazırlama hakkında ayrıntılı bilgi sunar.</span><span class="sxs-lookup"><span data-stu-id="e7010-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7010-107">Genel türlerin hazırlama desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e7010-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="e7010-108">Daha fazla bilgi için [birlikte kullanarak genel türler](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e7010-108">For more information see, [Interoperating Using Generic Types](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="e7010-109">Bellek yönetimi ile birlikte çalışma Sıralayıcı</span><span class="sxs-lookup"><span data-stu-id="e7010-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="e7010-110">Birlikte çalışma sıralayıcı tarafından yönetilmeyen kod ayrılan belleği boşaltmak her zaman çalışır.</span><span class="sxs-lookup"><span data-stu-id="e7010-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="e7010-111">Bu davranış COM bellek yönetimi kurallarıyla uyumlu, ancak yerel C++ yöneten kurallarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e7010-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="e7010-112">Karışıklığı önlemek için yerel C++ davranışı (hiçbir bellek boşaltma) öngörüyorsanız çıkabilir zaman platformu kullanılarak çağırma, hangi işaretçileri için bellek otomatik olarak boşaltır.</span><span class="sxs-lookup"><span data-stu-id="e7010-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="e7010-113">Örneğin, C++ DLL'den aşağıdaki yönetilmeyen yöntemi çağırma otomatik olarak diğer bellek boş değil.</span><span class="sxs-lookup"><span data-stu-id="e7010-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="e7010-114">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="e7010-114">Unmanaged signature</span></span>  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="e7010-115">Bununla birlikte, her bir platform çağırma olarak prototip yöntemi tanımlayın, yerini **BSTR** ile yazın bir <xref:System.String> yazın ve arama `MethodOne`, ortak dil çalışma zamanı serbest girişimlerini `b` iki kez.</span><span class="sxs-lookup"><span data-stu-id="e7010-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="e7010-116">Kullanarak hazırlama davranışı değiştirebilirsiniz <xref:System.IntPtr> türleri yerine **dize** türleri.</span><span class="sxs-lookup"><span data-stu-id="e7010-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="e7010-117">Çalışma zamanı her zaman kullanır **CoTaskMemFree** belleği boşaltmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="e7010-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="e7010-118">Çalıştığınız bellek ile ayrılmamış varsa **CoTaskMemAlloc** yöntemini kullanmalıdır bir **IntPtr** ve uygun yöntem kullanılarak el ile bellek boş.</span><span class="sxs-lookup"><span data-stu-id="e7010-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="e7010-119">Otomatik bellek boşaltma burada bellek hiçbir zaman serbest durumlarda, bu tür benzer şekilde, önleyebilirsiniz olarak kullanırken **GetCommandLine** çekirdek bellek için bir işaretçi döndürür Kernel32.dll işlevinden.</span><span class="sxs-lookup"><span data-stu-id="e7010-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="e7010-120">El ile bellek boşaltma hakkında daha fazla bilgi için bkz [arabellekleri örnek](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e7010-120">For details on manually freeing memory, see the [Buffers Sample](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="e7010-121">Varsayılan sınıflar için hazırlama</span><span class="sxs-lookup"><span data-stu-id="e7010-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="e7010-122">Sınıflar yalnızca COM birlikte çalışma tarafından sıralanabilir ve arabirimleri olarak her zaman hazırlanırlar.</span><span class="sxs-lookup"><span data-stu-id="e7010-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="e7010-123">Bazı durumlarda sınıfı sıralama için kullanılan arabirim sınıf arabirimi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="e7010-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="e7010-124">Tercih ettiğiniz bir arabirim ile sınıf arabirimi geçersiz kılma hakkında daha fazla bilgi için bkz: [sınıf arabirimi Tanıtımı](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="e7010-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="e7010-125">COM sınıflarına geçirme</span><span class="sxs-lookup"><span data-stu-id="e7010-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="e7010-126">Yönetilen bir sınıfın COM geçirildiğinde, birlikte çalışabilirlik Sıralayıcı otomatik olarak bir COM proxy ile sınıfı sarmalar ve COM yöntem çağrısı proxy'sine tarafından üretilen sınıf arabirimi geçirir.</span><span class="sxs-lookup"><span data-stu-id="e7010-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="e7010-127">Proxy sınıfı arabirimde tüm çağrıları yönetilen nesneye sonra atar.</span><span class="sxs-lookup"><span data-stu-id="e7010-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="e7010-128">Proxy sınıfı tarafından açıkça uygulanmadı diğer arabirimleri de sunar.</span><span class="sxs-lookup"><span data-stu-id="e7010-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="e7010-129">Proxy otomatik olarak arabirimlerini gibi uygular **IUnknown** ve **IDispatch** sınıfı adına.</span><span class="sxs-lookup"><span data-stu-id="e7010-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="e7010-130">.NET kodu için geçirme sınıfları</span><span class="sxs-lookup"><span data-stu-id="e7010-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="e7010-131">Coclass'ları genellikle COM yöntemi bağımsız değişken olarak kullanılan değil</span><span class="sxs-lookup"><span data-stu-id="e7010-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="e7010-132">Bunun yerine, varsayılan arabirimi genellikle yerine coclass'ı geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="e7010-133">Arabirim yönetilen koda geçirildiğinde, birlikte çalışabilirlik Sıralayıcı uygun sarmalayıcı arabirimiyle kaydırma ve yönetilen yöntemi sarmalayıcı geçirme sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e7010-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="e7010-134">Kullanmak için hangi sarmalayıcı zor olabilir belirleme.</span><span class="sxs-lookup"><span data-stu-id="e7010-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="e7010-135">Her bir COM nesnesinin örneği tek ve benzersiz bir sarmalayıcı nesne uygulayan kaç arabirimleri olsun sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e7010-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="e7010-136">Örneğin, beş farklı arabirimlerini uygular tek bir COM nesnesi yalnızca bir sarmalayıcı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e7010-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="e7010-137">Aynı sarmalayıcı tüm beş arabirimleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="e7010-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="e7010-138">COM nesnesi iki örneğini oluşturduysanız, sarmalayıcısı iki örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e7010-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="e7010-139">Sarmalayıcı yaşam süresi boyunca aynı türde korumak, nesne tarafından kullanıma sunulan bir arabirim Sıralayıcı geçirilen ilk kez doğru sarmalayıcı birlikte çalışma Sıralayıcı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7010-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="e7010-140">Sıralayıcı, bir nesne uygulayan arabirimleri at bakarak nesne tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7010-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="e7010-141">Örneğin, Sıralayıcı sınıfı sarmalayıcı yönetilen koda geçildi arabirimi sarmalamak için kullanılacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="e7010-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="e7010-142">Arabirimi Sıralayıcı ilk geçirildiğinde Sıralayıcı arabirimi bilinen bir nesneden gelen olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="e7010-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="e7010-143">Bu onay iki durumlarda gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="e7010-143">This check occurs in two situations:</span></span>  
  
-   <span data-ttu-id="e7010-144">Bir arabirim COM başka bir yerde geçildi başka bir yönetilen nesne tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e7010-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="e7010-145">Sıralayıcı yönetilen nesneler tarafından sergilenen arabirimlerle kolayca belirleyebilir ve uygulamasını sağlar Yönetilen Nesne arabirimiyle eşleşecek şekilde edebilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="e7010-146">Yönetilen Nesne sonra yönteme geçirilen ve hiçbir sarmalayıcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e7010-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
-   <span data-ttu-id="e7010-147">Zaten sarmalanmış bir nesne arabirimi uygulama.</span><span class="sxs-lookup"><span data-stu-id="e7010-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="e7010-148">Bu durumda olup olmadığını belirlemek için nesne için sıralayıcı sorgular kendi **IUnknown** arabirim ve diğer nesnelerin zaten Sarmalanan arabirimlerine döndürülen arabirimi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="e7010-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="e7010-149">Arabirim, başka bir sarmalayıcı aynı olduğunda, nesneleri aynı kimliğe sahip ve mevcut sarmalayıcı yönteme geçirilen.</span><span class="sxs-lookup"><span data-stu-id="e7010-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="e7010-150">Arabirim bilinen bir nesneden değilse, Sıralayıcı şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="e7010-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1.  <span data-ttu-id="e7010-151">Nesne için sıralayıcı sorgular **IProvideClassInfo2** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e7010-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="e7010-152">Sağlanırsa, döndürülen CLSID Sıralayıcı kullanan **IProvideClassInfo2.GetGUID** arabirim sağlayan coclass'ı tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="e7010-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="e7010-153">Derleme önceden kaydedilmişse CLSID ile kayıt defterinden sarmalayıcı Sıralayıcı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7010-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2.  <span data-ttu-id="e7010-154">Arabirim için sıralayıcı sorgular **IProvideClassInfo'yu** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e7010-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="e7010-155">Sağlanan, Sıralayıcı kullanıyorsa **ITypeInfo** döndürülen **IProvideClassInfo.GetClassinfo** arabirimi gösterme sınıfı CLSID belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="e7010-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="e7010-156">Sıralayıcı CLSID sarmalayıcı için meta verileri bulmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7010-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3.  <span data-ttu-id="e7010-157">Sıralayıcı hala sınıfı tanımlayamıyor, bir genel sarmalayıcı sınıfı adlı arabirimi sarmalar **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="e7010-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="e7010-158">Varsayılan temsilcileri sıralama</span><span class="sxs-lookup"><span data-stu-id="e7010-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="e7010-159">Yönetilen bir temsilci COM arabirimi veya arama mekanizmasını temel bir işlev işaretçisi olarak sıralanmış olduğundan:</span><span class="sxs-lookup"><span data-stu-id="e7010-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
-   <span data-ttu-id="e7010-160">İçin platform çağırma, bir temsilci varsayılan olarak bir yönetilmeyen işlev işaretçisi sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="e7010-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
-   <span data-ttu-id="e7010-161">COM birlikte çalışma için bir temsilci türü bir COM arabirimi sıralanmış **_Delegate** varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="e7010-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="e7010-162">**_Delegate** arabirimi Mscorlib.tlb tip Kitaplığı'nda tanımlanan ve içeren <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> temsilci başvuran yöntemini çağırmak sağlar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7010-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="e7010-163">Aşağıdaki tabloda, yönetilen temsilci veri türü için sıralama seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7010-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="e7010-164"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerleri sıralama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e7010-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="e7010-165">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="e7010-165">Enumeration type</span></span>|<span data-ttu-id="e7010-166">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="e7010-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="e7010-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="e7010-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="e7010-168">Bir yönetilmeyen işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e7010-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="e7010-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="e7010-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="e7010-170">Bir arabirim türü **_Delegate**, Mscorlib.tlb içinde tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="e7010-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="e7010-171">Aşağıdaki kod örneği, göz önünde bulundurun yöntemlerinin `DelegateTestInterface` bir COM tür kitaplığı dışarı aktarılır.</span><span class="sxs-lookup"><span data-stu-id="e7010-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="e7010-172">Yalnızca temsilci uyarısı işaretlenmiş **ref** (veya **ByRef**) anahtar sözcüğü olarak In/Out parametreleri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);     
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);    
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);   
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);     
}  
```  
  
### <a name="type-library-representation"></a><span data-ttu-id="e7010-173">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="e7010-173">Type library representation</span></span>  
  
```  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="e7010-174">Yalnızca başka bir yönetilmeyen işlev işaretçisi başvuru yapıldı gibi bir işlev işaretçisi, başvuru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="e7010-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="e7010-175">Bu örnekte, iki temsilcileri olarak sıralanmış zaman <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, sonuç bir `int` gösteren bir işaretçi bir `int`.</span><span class="sxs-lookup"><span data-stu-id="e7010-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="e7010-176">Temsilci türleri başvuruya çünkü `int` burada bir işaretçi bir geçersiz kılma temsil eder (`void*`), bellekte temsilci adresini olduğu.</span><span class="sxs-lookup"><span data-stu-id="e7010-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="e7010-177">Diğer bir deyişle, bu sonucu beri 32-bit Windows sistemleri için belirli `int` burada işlev işaretçisi boyutunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e7010-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
>  <span data-ttu-id="e7010-178">Yönetilmeyen kod tarafından tutulan yönetilen bir temsilci için işlev işaretçisi başvuru, yönetilen bir nesne üzerinde çöp toplama gerçekleştirme ortak dil çalışma zamanı engellemez.</span><span class="sxs-lookup"><span data-stu-id="e7010-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="e7010-179">Örneğin, aşağıdaki kodu yanlış olduğundan referansı `cb` geçirilen nesne `SetChangeHandler` yöntemi, tutmak değil `cb` ömrünü dışında tutma `Test` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7010-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="e7010-180">Bir kez `cb` nesne çöp toplama, işlev işaretçisi geçirilen `SetChangeHandler` artık geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e7010-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the   
      // object from being garbage collected after the Main method   
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));     
   }  
}  
```  
  
 <span data-ttu-id="e7010-181">Beklenmeyen atık toplama için dengelemek için arayan emin olmanız gerekir `cb` yönetilmeyen işlev işaretçisi kullanımda olduğu sürece nesne Canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="e7010-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="e7010-182">İsteğe bağlı olarak, yönetilen kod işlev işaretçisi artık, aşağıdaki örnekte gösterildiği gibi gerekli olduğunda bildir yönetilmeyen kod olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is   
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="e7010-183">Varsayılan değer türleri için hazırlama</span><span class="sxs-lookup"><span data-stu-id="e7010-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="e7010-184">Tamsayı ve kayan nokta sayıları gibi çoğu değer türleri [blittable](blittable-and-non-blittable-types.md) ve hazırlama gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="e7010-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="e7010-185">Diğer [blittable olmayan](blittable-and-non-blittable-types.md) türleri farklı Beyanları yönetilen ve yönetilmeyen bellekte ve hazırlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e7010-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="e7010-186">Hala diğer türleri arasında birlikte çalışabilirlik sınır açık biçimlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e7010-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="e7010-187">Bu konuda biçimlendirilmiş değer türleri üzerinde izleme bilgileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="e7010-187">This topic provides the follow information on formatted value types:</span></span>  
  
-   [<span data-ttu-id="e7010-188">Değer türleri platformunda kullanılan çağırma</span><span class="sxs-lookup"><span data-stu-id="e7010-188">Value Types Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [<span data-ttu-id="e7010-189">COM birlikte çalışma içinde kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="e7010-189">Value Types Used in COM Interop</span></span>](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 <span data-ttu-id="e7010-190">Biçimlendirilmiş türlerini açıklayan ek olarak, bu konu tanımlar [sistem değer türleri](#cpcondefaultmarshalingforvaluetypesanchor1) olağan dışı hazırlama davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e7010-190">In addition to describing formatted types, this topic identifies [System Value Types](#cpcondefaultmarshalingforvaluetypesanchor1) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="e7010-191">Açıkça üyeleri bellekte düzenini denetimleri bilgi içeren bir karmaşık türü bir biçimlendirilmiş türüdür.</span><span class="sxs-lookup"><span data-stu-id="e7010-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="e7010-192">Üye düzen bilgilerini kullanarak sağlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e7010-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="e7010-193">Düzeni aşağıdakilerden biri olabilir <xref:System.Runtime.InteropServices.LayoutKind> numaralandırma değerlerinin:</span><span class="sxs-lookup"><span data-stu-id="e7010-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
-   <span data-ttu-id="e7010-194">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="e7010-194">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="e7010-195">Ortak dil çalışma zamanı türü verimliliği için üyeleri yeniden sıralamak boş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7010-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="e7010-196">Ancak, bir değer türü yönetilmeyen koda geçirildiğinde üyeleri düzenini tahmin edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="e7010-197">Böyle bir yapı otomatik olarak sıralama girişimi bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="e7010-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
-   <span data-ttu-id="e7010-198">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="e7010-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="e7010-199">Tür üyeleri yönetilen tür tanımında göründükleri sırada yönetilmeyen bellekte düzenlendiği gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7010-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
-   <span data-ttu-id="e7010-200">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="e7010-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="e7010-201">Üyeleri göre düzenlenmiştir gösterir <xref:System.Runtime.InteropServices.FieldOffsetAttribute> her alanıyla sağlanan.</span><span class="sxs-lookup"><span data-stu-id="e7010-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="e7010-202">Değer türleri platformunda kullanılan çağırma</span><span class="sxs-lookup"><span data-stu-id="e7010-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="e7010-203">Aşağıdaki örnekte `Point` ve `Rect` türleri düzen bilgilerini üye sağlamak kullanarak **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="e7010-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 <span data-ttu-id="e7010-204">Yönetilmeyen kod için sıralanmış, bu biçimlendirilmiş türleri C tarzı yapıları olarak hazırlanırlar.</span><span class="sxs-lookup"><span data-stu-id="e7010-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="e7010-205">Bu yapı bağımsız değişkenlere sahiptir bir yönetilmeyen API çağırma için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7010-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="e7010-206">Örneğin, `POINT` ve `RECT` yapıları için Microsoft Win32 API geçirilebilir **PtInRect** gibi işlev:</span><span class="sxs-lookup"><span data-stu-id="e7010-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Win32 API **PtInRect** function as follows:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="e7010-207">Yapıları geçirebilirsiniz aşağıdaki platform kullanarak çağırma tanımı:</span><span class="sxs-lookup"><span data-stu-id="e7010-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb  
Class Win32API      
   Declare Auto Function PtInRect Lib "User32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("User32.dll")]  
   public static extern Bool PtInRect(ref Rect r, Point p);  
}  
```  
  
 <span data-ttu-id="e7010-208">`Rect` Değer türü gerekir bayraklarıdır başvuru tarafından yönetilmeyen API için bir işaretçi bekleniyor çünkü bir `RECT` işleve geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="e7010-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="e7010-209">`Point` Değer türü yönetilmeyen API beklediği değeri tarafından geçirilen `POINT` yığında geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="e7010-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="e7010-210">Bu fark çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e7010-210">This subtle difference is very important.</span></span> <span data-ttu-id="e7010-211">Başvuruları yönetilmeyen koda işaretçi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="e7010-212">Değerler yönetilmeyen koda yığında geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7010-213">Biçimlendirilmiş bir türü yapısı sıralanmış, yalnızca alanları türü içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="e7010-214">Yöntemler, özellikler veya olayların türündeyse, yönetilmeyen koddan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="e7010-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="e7010-215">Üye düzeni sabit koşuluyla sınıfları ayrıca yönetilmeyen koda C tarzı yapıları olarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="e7010-216">Bir sınıf için üye düzen bilgilerini de ile sağlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e7010-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="e7010-217">Değer türleri ile arasındaki temel fark düzeni sabit ve sabit düzeni sınıflarıyla, yönetilmeyen koda sıralanmış yoludur.</span><span class="sxs-lookup"><span data-stu-id="e7010-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="e7010-218">Değer türleri (yığında) değeriyle geçirilir ve sonuç olarak türün üyeleri Aranan tarafından yapılan değişiklikler çağıran tarafından görülmez.</span><span class="sxs-lookup"><span data-stu-id="e7010-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="e7010-219">Başvuru türleri (türüne bir başvuru yığında geçirilen) başvuruya göre geçirilir; Sonuç olarak, bir tür blittable türü üyelerine Aranan tarafından yapılan tüm değişiklikler çağıran tarafından görülür.</span><span class="sxs-lookup"><span data-stu-id="e7010-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7010-220">Bir başvuru türü kopyalanamaz türler üyeleri varsa dönüştürme iki kez gerekli değildir: ne zaman bir bağımsız değişken geçirilir yönetilmeyen yan ve ikinci ilk kez zaman çağrısından döndürülen.</span><span class="sxs-lookup"><span data-stu-id="e7010-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="e7010-221">Aranan tarafından yapılan değişiklikleri görmek arayan istiyorsa, bunu nedeniyle yükü eklenen parametreleri giriş/çıkış açıkça bir bağımsız uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7010-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="e7010-222">Aşağıdaki örnekte, `SystemTime` sınıfı sıralı üye düzenine sahip ve Win32 API geçirilebilir **GetSystemTime** işlevi.</span><span class="sxs-lookup"><span data-stu-id="e7010-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Win32 API **GetSystemTime** function.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;   
   public ushort wMonth;  
   public ushort wDayOfWeek;   
   public ushort wDay;   
   public ushort wHour;   
   public ushort wMinute;   
   public ushort wSecond;   
   public ushort wMilliseconds;   
}  
```  
  
 <span data-ttu-id="e7010-223">**GetSystemTime** işlevi aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="e7010-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="e7010-224">Eşdeğer platform çağırma tanımı **GetSystemTime** aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e7010-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb  
Public Class Win32  
   Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (ByVal sysTime _  
   As SystemTime)  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("Kernel32.dll", CharSet=CharSet.Auto)]  
   public static extern void GetSystemTime(SystemTime st);  
}  
```  
  
 <span data-ttu-id="e7010-225">Dikkat `SystemTime` olduğundan bağımsız değişkeni bir başvuru bağımsız değişkeni değil yazılan `SystemTime` bir sınıf, bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="e7010-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="e7010-226">Değer türlerinin aksine, sınıflar her zaman başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="e7010-227">Aşağıdaki kod örneği farklı bir gösterir `Point` adlı bir yöntemi olan sınıfı `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="e7010-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="e7010-228">Ardışık Düzen türüne sahip olduğundan, yönetilmeyen kod için geçirilen ve yapısı olarak sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="e7010-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="e7010-229">Ancak, `SetXY` üyesi olmayan yönetilmeyen koddan çağrılabilir rağmen başvuruya göre nesnesi geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e7010-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){   
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor3"></a>   
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="e7010-230">COM birlikte çalışma içinde kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="e7010-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="e7010-231">Biçimlendirilmiş türleri COM birlikte çalışma yöntem çağrıları için de geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="e7010-232">Aslında, bir tür kitaplığı dışarı aktardığınızda değer türleri otomatik olarak yapılara dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="e7010-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="e7010-233">Aşağıdaki örnekte gösterildiği gibi `Point` değer türü olur (typedef) adlı bir tür tanımı `Point`.</span><span class="sxs-lookup"><span data-stu-id="e7010-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="e7010-234">Tüm başvuruları `Point` başka bir tür kitaplığı içinde değer türüne değiştirildiğini `Point` typedef.</span><span class="sxs-lookup"><span data-stu-id="e7010-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="e7010-235">**Tür kitaplığı gösterimi**</span><span class="sxs-lookup"><span data-stu-id="e7010-235">**Type library representation**</span></span>  
  
```  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 <span data-ttu-id="e7010-236">Değerleri ve platform başvurular sıralama için kullanılan aynı kuralları çağrıları çağırma COM arabirimleri aracılığıyla sıralama sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7010-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="e7010-237">Örneğin, bir örneği olduğunda `Point` değer türü, COM .NET Framework'teki geçirilen `Point` değeri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="e7010-238">Varsa `Point` değer türü başvurusu, bir işaretçi olarak geçirilir bir `Point` yığında geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7010-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="e7010-239">Birlikte çalışma Sıralayıcı yöneltme daha yüksek düzeyde desteklemez (**noktası** \* \*) her iki yönde.</span><span class="sxs-lookup"><span data-stu-id="e7010-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7010-240">Yapıları sahip <xref:System.Runtime.InteropServices.LayoutKind> numaralandırma değeri ayarlamak **Explicit** verilen tür kitaplığı açık bir düzen express yapılamıyor çünkü COM birlikte çalışma içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e7010-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a><span data-ttu-id="e7010-241">Sistem değer türleri</span><span class="sxs-lookup"><span data-stu-id="e7010-241">System Value Types</span></span>  
 <span data-ttu-id="e7010-242"><xref:System> Ad alanına sahip çalışma zamanı ilkel türler Kutulu biçiminde temsil eden birkaç değer türleri.</span><span class="sxs-lookup"><span data-stu-id="e7010-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="e7010-243">Örneğin, değer türü <xref:System.Int32?displayProperty=nameWithType> yapısını temsil eden Kutulu biçiminde **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="e7010-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="e7010-244">Biçimlendirilmiş diğer türleri gibi bu tür yapıları olarak hazırlama yerine, bunları bunlar kutusunda ilkel türler aynı şekilde sıralama.</span><span class="sxs-lookup"><span data-stu-id="e7010-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="e7010-245">**System.Int32** bu nedenle olarak sıralanmış **ELEMENT_TYPE_I4** yerine türü tek bir üyeyi içeren bir yapı olarak **uzun**.</span><span class="sxs-lookup"><span data-stu-id="e7010-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="e7010-246">Aşağıdaki tabloda değer türlerinin bir listesini içeren **sistem** paketlenmiş gösterimlerini ilkel türleri olan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e7010-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="e7010-247">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="e7010-247">System value type</span></span>|<span data-ttu-id="e7010-248">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="e7010-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="e7010-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="e7010-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="e7010-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="e7010-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="e7010-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="e7010-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="e7010-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="e7010-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="e7010-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="e7010-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="e7010-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="e7010-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="e7010-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="e7010-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="e7010-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="e7010-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="e7010-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="e7010-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="e7010-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="e7010-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="e7010-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="e7010-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="e7010-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="e7010-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="e7010-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="e7010-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="e7010-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="e7010-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="e7010-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="e7010-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="e7010-264">Başka bir değer türleri **sistem** ad alanı farklı bir şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="e7010-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="e7010-265">Yönetilmeyen kod bu tür tanınmış biçimleri zaten sahip olduğu Sıralayıcı bunları hazırlama için özel kurallar vardır.</span><span class="sxs-lookup"><span data-stu-id="e7010-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="e7010-266">Aşağıdaki tabloda özel değer türlerini listeler **sistem** ad alanı, bunlar için hazırlanır yönetilmeyen tür yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="e7010-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="e7010-267">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="e7010-267">System value type</span></span>|<span data-ttu-id="e7010-268">IDL türü</span><span class="sxs-lookup"><span data-stu-id="e7010-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="e7010-269">**TARİH**</span><span class="sxs-lookup"><span data-stu-id="e7010-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="e7010-270">**ONDALIK**</span><span class="sxs-lookup"><span data-stu-id="e7010-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="e7010-271">**GUID**</span><span class="sxs-lookup"><span data-stu-id="e7010-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="e7010-272">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="e7010-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="e7010-273">Aşağıdaki kod yönetilmeyen türlerinin tanımını gösterir **tarih**, **GUID**, **ondalık**, ve **OLE_COLOR** Stdole2 türü Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="e7010-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="e7010-274">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="e7010-274">Type library representation</span></span>  
  
```  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 <span data-ttu-id="e7010-275">Aşağıdaki kod karşılık gelen tanımları yönetilen gösterir `IValueTypes` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e7010-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a><span data-ttu-id="e7010-276">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="e7010-276">Type library representation</span></span>  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7010-277">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7010-277">See Also</span></span>  
 [<span data-ttu-id="e7010-278">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="e7010-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="e7010-279">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="e7010-279">Copying and Pinning</span></span>](copying-and-pinning.md)  
 [<span data-ttu-id="e7010-280">Diziler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e7010-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)  
 [<span data-ttu-id="e7010-281">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e7010-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)  
 [<span data-ttu-id="e7010-282">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e7010-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
