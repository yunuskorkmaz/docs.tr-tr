---
title: Varsayılan Sıralama Davranışı
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
ms.openlocfilehash: c6de6091b8970fde4a958148acf32dcefe1a6726
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946553"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="987ed-102">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="987ed-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="987ed-103">Birlikte çalışabilirlik sıralaması, yöntem parametreleriyle ilişkili verilerin yönetilen ve yönetilmeyen bellek arasında geçerken nasıl davranacağını dikte eden kurallar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="987ed-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="987ed-104">Bu yerleşik kurallar, verileri veri türü dönüşümleri olarak sıralama, bir çağrılan verilerin kendisine geçirilen verileri değiştirip çağıramayacağını ve bu değişiklikleri arayana döndürmesini ve bu değişiklikleri, Sıralayıcı 'nın performans iyileştirmeleri sağladığı koşullarda değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="987ed-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="987ed-105">Bu bölüm, birlikte çalışma sıralama hizmetinin varsayılan davranış özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="987ed-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="987ed-106">Dizileri, Boole türlerini, karakter türlerini, temsilcileri, sınıfları, nesneleri, dizeleri ve yapıları hazırlama hakkında ayrıntılı bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="987ed-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="987ed-107">Genel türlerin sıralaması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="987ed-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="987ed-108">Daha fazla bilgi için bkz. [Genel türler kullanılarak birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="987ed-108">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="987ed-109">Birlikte çalışma sıralayıcısı ile bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="987ed-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="987ed-110">Birlikte çalışma sıralayıcısı, her zaman yönetilmeyen kod tarafından ayrılan belleği serbest bırakma girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="987ed-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="987ed-111">Bu davranış, COM bellek yönetimi kurallarına uyar, ancak yerel C++' i yöneten kurallardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="987ed-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="987ed-112">Platform çağırma kullanılırken yerel C++ davranışı (bellek boşaltma yok) tahmin etmeniz durumunda karışıklığa neden olabilir ve bu da işaretçiler için belleği otomatik olarak boşaltır.</span><span class="sxs-lookup"><span data-stu-id="987ed-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="987ed-113">Örneğin, bir dll 'den aşağıdaki yönetilmeyen yöntemi çağırmak herhangi C++ bir belleği otomatik olarak serbest vermez.</span><span class="sxs-lookup"><span data-stu-id="987ed-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="987ed-114">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="987ed-114">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="987ed-115">Ancak, yöntemi bir platform çağırma prototipi olarak tanımlarsanız, her **BSTR** türünü bir <xref:System.String> tür ile değiştirin ve çağırın `MethodOne`, ortak dil çalışma zamanı iki kez ücretsiz `b` olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="987ed-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="987ed-116">Sıralama davranışını <xref:System.IntPtr> **dize** türleri yerine türler kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="987ed-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="987ed-117">Çalışma zamanı, belleği boşaltmak için her zaman **CoTaskMemFree** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="987ed-118">Çalıştığınız bellek **CoTaskMemAlloc** yöntemiyle ayrıldıysa, bir **IntPtr** kullanmanız ve uygun yöntemi kullanarak belleği el ile boşaltmalısınız.</span><span class="sxs-lookup"><span data-stu-id="987ed-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="987ed-119">Benzer şekilde, çekirdek belleğine bir işaretçi döndüren Kernel32. dll ' den **GetCommandLine** işlevi kullanılırken, belleğin asla boşaltılmaması gereken durumlarda otomatik bellek boşaltmasını önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="987ed-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="987ed-120">Belleği el ile boşaltma hakkında ayrıntılı bilgi için bkz. [arabellekler örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="987ed-120">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="987ed-121">Sınıflar için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="987ed-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="987ed-122">Sınıflar yalnızca COM birlikte çalışabilirliğine göre sıralanabilir ve her zaman arabirim olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="987ed-123">Bazı durumlarda, sınıfı sıralamak için kullanılan arabirim sınıf arabirimi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="987ed-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="987ed-124">Sınıf arabirimini tercih ettiğiniz bir arabirimle geçersiz kılma hakkında daha fazla bilgi için bkz. [sınıf arabirimine giriş](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="987ed-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="987ed-125">Sınıfları COM 'a geçirme</span><span class="sxs-lookup"><span data-stu-id="987ed-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="987ed-126">Yönetilen bir sınıf COM 'a geçirildiğinde, birlikte çalışma sıralayıcısı otomatik olarak sınıfı bir COM proxy 'si ile sarmalanmış ve proxy tarafından üretilen sınıf arabirimini COM yöntem çağrısına geçirir.</span><span class="sxs-lookup"><span data-stu-id="987ed-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="987ed-127">Ardından ara sunucu, sınıf arabirimindeki tüm çağrıları yönetilen nesneye yeniden devreder.</span><span class="sxs-lookup"><span data-stu-id="987ed-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="987ed-128">Proxy Ayrıca, sınıfı tarafından açıkça uygulanmayan diğer arabirimleri de kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="987ed-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="987ed-129">Proxy, sınıf adına **IUnknown** ve **IDispatch** gibi arabirimleri otomatik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="987ed-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="987ed-130">Sınıfları .NET koduna geçirme</span><span class="sxs-lookup"><span data-stu-id="987ed-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="987ed-131">Ortak sınıflar genellikle COM 'da Yöntem bağımsız değişkenleri olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="987ed-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="987ed-132">Bunun yerine, varsayılan bir arabirim genellikle coclass 'ın yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="987ed-133">Bir arabirim yönetilen koda geçirildiğinde, birlikte çalışma sıralayıcısı, arabirimin doğru sarmalayıcı ile sarmalanması ve sarmalayıcı yönetilen yönteme geçirilmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="987ed-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="987ed-134">Hangi sarmalayıcı kullanacağınızı belirlemek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="987ed-135">Bir COM nesnesinin her örneği, nesnenin kaç arabirim uyguladığını fark etmeksizin tek ve benzersiz bir sarmalayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="987ed-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="987ed-136">Örneğin, beş farklı arabirimi uygulayan tek bir COM nesnesi yalnızca bir sarmalayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="987ed-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="987ed-137">Aynı sarmalayıcı beş arabirimi de kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="987ed-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="987ed-138">COM nesnesinin iki örneği oluşturulursa, sarmalayıcının iki örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="987ed-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="987ed-139">Sarmalayıcının ömrü boyunca aynı türü koruabilmesi için, nesne tarafından kullanıma sunulan bir arabirim Sıralayıcı üzerinden geçirildiğinde, birlikte çalışma sıralayıcısı doğru sarmalayıcı tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="987ed-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="987ed-140">Sıralayıcı nesnenin uyguladığı arayüzlerden birine bakarak nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="987ed-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="987ed-141">Örneğin Sıralayıcı, sınıf sarmalayıcının yönetilen koda geçirilen arabirimi sarmalamak için kullanılması gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="987ed-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="987ed-142">Arabirim Sıralayıcı tarafından ilk kez geçirildiğinde Sıralayıcı, arabirimin bilinen bir nesneden geliyor olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="987ed-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="987ed-143">Bu denetim iki durumda gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="987ed-143">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="987ed-144">Bir arabirim, COM 'a başka bir yerde geçirilmiş başka bir yönetilen nesne tarafından uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="987ed-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="987ed-145">Sıralayıcı yönetilen nesneler tarafından sunulan arabirimleri kolayca tanımlayabilir ve arabirimi, uygulamayı sağlayan yönetilen nesneyle eşleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="987ed-146">Yönetilen nesne daha sonra yönteme geçirilir ve sarmalayıcı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="987ed-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="987ed-147">Zaten sarmalanmış bir nesne arabirimini uygulama.</span><span class="sxs-lookup"><span data-stu-id="987ed-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="987ed-148">Bunun durum olup olmadığını anlamak için sıralayıcı, nesneyi **IUnknown** arabirimine sorgular ve döndürülen arabirimi zaten sarmalanmış diğer nesnelerin arabirimlerine karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="987ed-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="987ed-149">Arabirim, başka bir sarmalayıcı ile aynıysa, nesneler aynı kimliğe sahip olur ve varolan sarmalayıcı yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="987ed-150">Bir arabirim bilinen bir nesneden değilse Sıralayıcı şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="987ed-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="987ed-151">Sıralayıcı, **IProvideClassInfo2** arabirimi için nesneyi sorgular.</span><span class="sxs-lookup"><span data-stu-id="987ed-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="987ed-152">Sağlanmışsa, Sıralayıcı, arabirimi sağlayan coclass 'ı tanımlamak için **IProvideClassInfo2. GetGUID** ÖĞESINDEN döndürülen CLSID 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="987ed-153">CLSID ile, derleme daha önce kaydedilmişse, Sıralayıcı kayıt defterinden sarmalayıcı bulabilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="987ed-154">Sıralayıcı, **IProvideClassInfo** arabirimi için arabirimi sorgular.</span><span class="sxs-lookup"><span data-stu-id="987ed-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="987ed-155">Belirtilmişse, Sıralayıcı, arabirimi kullanıma sunmadan sınıfın CLSID 'sini belirlemede **IProvideClassInfo. GetClassInfo** öğesinden döndürülen **ITypeInfo bilgisini** kullanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="987ed-156">Sıralayıcı, sarmalayıcının meta verilerini bulmak için CLSID 'yi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="987ed-157">Sıralayıcı hala sınıfı tanımlayamıyor, arabirimi **System. __ComObject**adlı bir genel sarmalayıcı sınıfıyla sarmalanmış olur.</span><span class="sxs-lookup"><span data-stu-id="987ed-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="987ed-158">Temsilciler için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="987ed-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="987ed-159">Yönetilen bir temsilci, çağırma mekanizmasına bağlı olarak bir COM arabirimi veya bir işlev işaretçisi olarak sıralanır:</span><span class="sxs-lookup"><span data-stu-id="987ed-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="987ed-160">Platform çağırma için bir temsilci varsayılan olarak yönetilmeyen bir işlev işaretçisi olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="987ed-161">COM birlikte çalışması için bir temsilci, varsayılan olarak **_Delegate** türünde bir com arabirimi olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="987ed-162">**_Delegate** arabirimi mscorlib. tlb tür kitaplığında tanımlanmıştır ve temsilcinin başvurduğu yöntemi çağırabilmenizi sağlayan <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="987ed-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="987ed-163">Aşağıdaki tabloda, yönetilen temsilci veri türü için sıralama seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="987ed-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="987ed-164">Özniteliği <xref:System.Runtime.InteropServices.MarshalAsAttribute> , temsilcileri sıralamak <xref:System.Runtime.InteropServices.UnmanagedType> için birkaç numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="987ed-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="987ed-165">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="987ed-165">Enumeration type</span></span>|<span data-ttu-id="987ed-166">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="987ed-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="987ed-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="987ed-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="987ed-168">Yönetilmeyen bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="987ed-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="987ed-169">**UnmanagedType. Interface**</span><span class="sxs-lookup"><span data-stu-id="987ed-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="987ed-170">Mscorlib. tlb içinde tanımlandığı şekilde **_Delegate**türünde bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="987ed-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="987ed-171">Yöntemlerinin `DelegateTestInterface` bir com tür kitaplığına aktarılması için aşağıdaki örnek kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="987ed-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="987ed-172">Yalnızca **ref** (veya **ByRef**) anahtar sözcüğüyle Işaretlenen temsilcilerin ın/out parametrelerine geçtiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="987ed-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="987ed-173">Tür kitaplığı temsili</span><span class="sxs-lookup"><span data-stu-id="987ed-173">Type library representation</span></span>  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="987ed-174">Bir işlev işaretçisine, diğer yönetilmeyen işlev işaretçilerine başvurulanlar gibi başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="987ed-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="987ed-175">Bu örnekte, iki temsilci olarak <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>sıralandığınızda, sonuç bir `int` `int`ve bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="987ed-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="987ed-176">Temsilci türleri sıralanmakta olduğundan, `int` bu, bellekteki temsilcinin adresi olan void (`void*`) için bir işaretçi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="987ed-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="987ed-177">Diğer bir deyişle, bu sonuç 32 bitlik Windows sistemlerine özgüdür, `int` bu nedenle işlev işaretçisinin boyutunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="987ed-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="987ed-178">Yönetilmeyen kod tarafından tutulan yönetilen bir temsilciye yönelik işlev işaretçisine yönelik bir başvuru, ortak dil çalışma zamanının yönetilen nesnede çöp toplama gerçekleştirmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="987ed-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="987ed-179">`cb` Örneğin, `SetChangeHandler` yönteminegeçirilen`Test` nesneye yapılan başvuru, yöntemin ömrünün ötesinde etkinolmadığından,aşağıdakikodyanlış.`cb`</span><span class="sxs-lookup"><span data-stu-id="987ed-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="987ed-180">Nesne çöp topladıktan sonra, `SetChangeHandler` geçirilen işlev işaretçisi artık geçerli değildir. `cb`</span><span class="sxs-lookup"><span data-stu-id="987ed-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="987ed-181">Beklenmedik atık toplamayı dengelemek için çağıran, yönetilmeyen işlev işaretçisi kullanımda olduğu sürece `cb` nesnenin canlı tutulduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="987ed-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="987ed-182">İsteğe bağlı olarak, aşağıdaki örnekte gösterildiği gibi, işlev işaretçisine artık ihtiyaç duyulmadığında, yönetilmeyen kodun yönetilen koda bildirilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="987ed-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="987ed-183">Değer türleri için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="987ed-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="987ed-184">Tamsayılar ve kayan nokta numaraları gibi çoğu değer türleri [blittable](blittable-and-non-blittable-types.md) ve sıralama gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="987ed-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="987ed-185">Diğer [blittable dışı](blittable-and-non-blittable-types.md) türler yönetilen ve yönetilmeyen bellekte benzer temsiller ve sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="987ed-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="987ed-186">Hala diğer türler, birlikte çalışma sınırları genelinde açık biçimlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="987ed-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="987ed-187">Bu bölüm aşağıdaki biçimli değer türleri hakkında bilgi sağlar:</span><span class="sxs-lookup"><span data-stu-id="987ed-187">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="987ed-188">Platform çağırmada kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="987ed-188">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="987ed-189">COM birlikte çalışabilirliğine kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="987ed-189">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="987ed-190">Bu konuda, biçimlendirilen türlerin açıklanmasına ek olarak, olağan dışı sıralama davranışına sahip [Sistem değeri türleri](#system-value-types) tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="987ed-190">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="987ed-191">Biçimlendirilen bir tür, içindeki üyelerinin doğrudan, bellekteki yerleşimini açıkça denetleyen bilgiler içeren karmaşık bir türdür.</span><span class="sxs-lookup"><span data-stu-id="987ed-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="987ed-192">Üye düzen bilgileri, <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="987ed-193">Düzen aşağıdaki <xref:System.Runtime.InteropServices.LayoutKind> sabit listesi değerlerinden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="987ed-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="987ed-194">**LayoutKind. Automatic**</span><span class="sxs-lookup"><span data-stu-id="987ed-194">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="987ed-195">Ortak dil çalışma zamanının, verimlilik için tür üyelerini yeniden sıralamak için boş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="987ed-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="987ed-196">Ancak, bir değer türü yönetilmeyen koda geçirildiğinde, üyelerin düzeni öngörülebilir olur.</span><span class="sxs-lookup"><span data-stu-id="987ed-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="987ed-197">Böyle bir yapıyı sıralama girişimi özel duruma otomatik olarak neden olur.</span><span class="sxs-lookup"><span data-stu-id="987ed-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="987ed-198">**LayoutKind. Sequential**</span><span class="sxs-lookup"><span data-stu-id="987ed-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="987ed-199">Türün üyelerinin yönetilmeyen bellekte, yönetilen tür tanımında göründükleri sırada düzenleneceğini gösterir...</span><span class="sxs-lookup"><span data-stu-id="987ed-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="987ed-200">**LayoutKind. Explicit**</span><span class="sxs-lookup"><span data-stu-id="987ed-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="987ed-201">Üyelerin her alanla <xref:System.Runtime.InteropServices.FieldOffsetAttribute> sağlanan öğesine göre düzenlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="987ed-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="987ed-202">Platform çağırmada kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="987ed-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="987ed-203">Aşağıdaki örnekte, `Point` ve `Rect` türleri **StructLayoutAttribute**kullanarak üye düzen bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="987ed-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="987ed-204">Yönetilmeyen koda sıralandığınızda, bu biçimli türler C stili yapılar olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="987ed-205">Bu, yapı bağımsız değişkenlerine sahip yönetilmeyen bir API çağırmanın kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="987ed-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="987ed-206">Örneğin, `POINT` ve `RECT` yapıları Microsoft Windows API **ptinrect** işlevine aşağıdaki gibi geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="987ed-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="987ed-207">Aşağıdaki platform çağırma tanımını kullanarak yapıları geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="987ed-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="987ed-208">Yönetilmeyen API, işleve geçirilecek bir işaretçi beklediği `RECT` için değertürübaşvuruyagöregeçirilmelidir.`Rect`</span><span class="sxs-lookup"><span data-stu-id="987ed-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="987ed-209">Yönetilmeyen API 'nin `POINT` yığına geçirilmesini beklediği için değertürüdeğeregöregeçirilir.`Point`</span><span class="sxs-lookup"><span data-stu-id="987ed-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="987ed-210">Bu hafif fark çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="987ed-210">This subtle difference is very important.</span></span> <span data-ttu-id="987ed-211">Başvurular yönetilmeyen koda işaretçiler olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="987ed-212">Değerler yığında yönetilmeyen koda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="987ed-213">Biçimlendirilen bir tür yapı olarak sıralanmışsa, yalnızca tür içindeki alanlara erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="987ed-214">Türün yöntemleri, özellikleri veya olayları varsa, bunlar yönetilmeyen koddan erişilmez.</span><span class="sxs-lookup"><span data-stu-id="987ed-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="987ed-215">Sınıflar, Ayrıca, sabit üye düzenine sahip olmaları şartıyla, yönetilmeyen koda C stili yapılar olarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="987ed-216">Bir sınıf için üye düzen bilgileri de <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğiyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="987ed-217">Sabit düzen ve sınıflar ile değer türleri arasındaki temel fark, yönetilmeyen kod için sıralandıkları yoldur.</span><span class="sxs-lookup"><span data-stu-id="987ed-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="987ed-218">Değer türleri değeri (yığında) ile geçirilir ve sonuç olarak, aranan tarafından türün üyelerinde yapılan değişiklikler arayan tarafından görülmez.</span><span class="sxs-lookup"><span data-stu-id="987ed-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="987ed-219">Başvuru türleri başvuruya göre geçirilir (türe bir başvuru yığına geçirilir); Sonuç olarak, aranan tarafından bir türün blittable-Type üyelerinde yapılan tüm değişiklikler arayan tarafından görülür.</span><span class="sxs-lookup"><span data-stu-id="987ed-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="987ed-220">Bir başvuru türünde blittable olmayan türlerde Üyeler varsa, dönüştürme iki kez gereklidir: bir bağımsız değişkenin yönetilmeyen tarafa geçirilmesi ve çağrıdan ikinci kez döndürülmesinin ilk zamanı.</span><span class="sxs-lookup"><span data-stu-id="987ed-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="987ed-221">Bu eklenen ek yük nedeniyle, çağıran tarafından yapılan değişiklikleri görmek istiyorsa, ın/out parametreleri açıkça bir bağımsız değişkene uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="987ed-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="987ed-222">Aşağıdaki örnekte, `SystemTime` sınıfı sıralı üye düzenine sahiptir ve Windows API **GetSystemTime** işlevine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="987ed-223">**GetSystemTime** işlevi şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="987ed-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="987ed-224">**GetSystemTime** için eşdeğer platform çağırma tanımı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="987ed-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="987ed-225">`SystemTime` Bağımsız değişkenin bir başvuru `SystemTime` bağımsız değişkeni olarak yazılmadığından, bir değer türü değil bir sınıf olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="987ed-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="987ed-226">Değer türlerinin aksine, sınıflar her zaman başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="987ed-227">Aşağıdaki kod örneği, adlı `Point` `SetXY`bir yöntemi olan farklı bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="987ed-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="987ed-228">Türün sıralı düzeni olduğundan, yönetilmeyen koda geçirilebilir ve bir yapı olarak sıralanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="987ed-229">Ancak, `SetXY` nesne başvuru ile geçirilse bile, yönetilmeyen koddan üye çağrılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="987ed-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="987ed-230">COM birlikte çalışabilirliğine kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="987ed-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="987ed-231">Biçimlendirilen türler, COM birlikte çalışma yöntemi çağrılarına de geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="987ed-232">Aslında, bir tür kitaplığına aktarıldığında, değer türleri otomatik olarak yapılara dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="987ed-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="987ed-233">Aşağıdaki örnekte gösterildiği gibi, `Point` değer türü adıyla `Point`bir tür tanımı (typedef) olur.</span><span class="sxs-lookup"><span data-stu-id="987ed-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="987ed-234">Tür kitaplığının başka bir `Point` yerinde değer türüne yapılan tüm başvurular `Point` typedef ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="987ed-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="987ed-235">**Tür kitaplığı temsili**</span><span class="sxs-lookup"><span data-stu-id="987ed-235">**Type library representation**</span></span>  
  
```cpp  
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
  
 <span data-ttu-id="987ed-236">Değerleri ve platform çağırma çağrılarına başvuruları sıralamak için kullanılan kurallar, COM arabirimleri üzerinden sıralama yapılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="987ed-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="987ed-237">Örneğin, `Point` değer türünün bir örneği .NET Framework com `Point` 'a geçirildiğinde, değeri tarafından geçirilir.</span><span class="sxs-lookup"><span data-stu-id="987ed-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="987ed-238">Değer türü başvuruya göre geçirilirse, yığına bir `Point` işaretçisi geçirilir. `Point`</span><span class="sxs-lookup"><span data-stu-id="987ed-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="987ed-239">Birlikte çalışma sıralayıcısı, iki yönde de daha yüksek yöneltme (**nokta** \* \*) düzeylerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="987ed-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="987ed-240"><xref:System.Runtime.InteropServices.LayoutKind> Sabit listesi değeri **Açık** olarak ayarlanmış olan yapılar, içe aktarılmış tür kitaplığı açık bir düzen ifade ettiğinden, com birlikte çalışma içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="987ed-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="987ed-241">Sistem değer türleri</span><span class="sxs-lookup"><span data-stu-id="987ed-241">System Value Types</span></span>  
 <span data-ttu-id="987ed-242"><xref:System> Ad alanı, çalışma zamanı temel türlerinin paketlenmiş formunu temsil eden çeşitli değer türlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="987ed-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="987ed-243">Örneğin, değer türü <xref:System.Int32?displayProperty=nameWithType> yapısı, **ELEMENT_TYPE_I4**kutulanmış formunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="987ed-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="987ed-244">Bu türleri yapılar olarak sıralamak yerine, diğer biçimlendirilen türler olduğu gibi, bunları kendi temel türleriyle aynı şekilde sıralamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="987ed-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="987ed-245">Bu nedenle **System. Int32** , **Long**türünde tek bir üye içeren bir yapı olarak değil **ELEMENT_TYPE_I4** olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="987ed-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="987ed-246">Aşağıdaki tablo, temel türlerin kutulanmış temsilleri olan **sistem** ad alanındaki değer türlerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="987ed-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="987ed-247">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="987ed-247">System value type</span></span>|<span data-ttu-id="987ed-248">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="987ed-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="987ed-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="987ed-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="987ed-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="987ed-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="987ed-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="987ed-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="987ed-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="987ed-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="987ed-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="987ed-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="987ed-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="987ed-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="987ed-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="987ed-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="987ed-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="987ed-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="987ed-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="987ed-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="987ed-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="987ed-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="987ed-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="987ed-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="987ed-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="987ed-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="987ed-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="987ed-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="987ed-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="987ed-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="987ed-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="987ed-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="987ed-264">**Sistem** ad alanındaki bazı diğer değer türleri farklı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="987ed-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="987ed-265">Yönetilmeyen kodun bu türler için zaten iyi belirlenmiş biçimleri olduğundan, Sıralayıcı bunları hazırlamayı sağlayacak özel kurallara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="987ed-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="987ed-266">Aşağıdaki tabloda, **sistem** ad alanındaki özel değer türlerinin yanı sıra, sıralandıkları yönetilmeyen tür listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="987ed-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="987ed-267">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="987ed-267">System value type</span></span>|<span data-ttu-id="987ed-268">IDL türü</span><span class="sxs-lookup"><span data-stu-id="987ed-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="987ed-269">**GÜNCEL**</span><span class="sxs-lookup"><span data-stu-id="987ed-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="987ed-270">**KATEGORI**</span><span class="sxs-lookup"><span data-stu-id="987ed-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="987ed-271">**GUID**</span><span class="sxs-lookup"><span data-stu-id="987ed-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="987ed-272">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="987ed-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="987ed-273">Aşağıdaki kod, Stdole2 tür kitaplığındaki yönetilmeyen türler **Tarih**, **GUID**, **DECIMAL**ve **OLE_COLOR** tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="987ed-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="987ed-274">Tür kitaplığı temsili</span><span class="sxs-lookup"><span data-stu-id="987ed-274">Type library representation</span></span>  
  
```cpp  
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
  
 <span data-ttu-id="987ed-275">Aşağıdaki kod, yönetilen `IValueTypes` arabirimde karşılık gelen tanımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="987ed-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="987ed-276">Tür kitaplığı temsili</span><span class="sxs-lookup"><span data-stu-id="987ed-276">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="987ed-277">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="987ed-277">See also</span></span>

- [<span data-ttu-id="987ed-278">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="987ed-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="987ed-279">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="987ed-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="987ed-280">Diziler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="987ed-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="987ed-281">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="987ed-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="987ed-282">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="987ed-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
