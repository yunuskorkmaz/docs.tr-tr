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
ms.openlocfilehash: f7df323dacfbee3361fe75d831f1e87df328b194
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989226"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="5eaf8-102">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="5eaf8-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="5eaf8-103">Interop marshaling, yöntem parametreleri ile ilişkili verilerin yönetilen ve yönetilmeyen bellekler arasında geçerken nasıl çalıştığını belirleyen kurallar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="5eaf8-104">Bu yerleşik kurallar, veri türü dönüşümleri, bir callee'nin ona aktarılan verileri değiştirip değiştiremeyeceği ve bu değişiklikleri arayana döndürüp döndüremeyeceği ve mareşalin performans optimizasyonları sağladığı koşullar altında bu tür etkinliklerin denetlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="5eaf8-105">Bu bölümde, interop mareşallik hizmetinin varsayılan davranış özellikleri tanımnıla.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="5eaf8-106">Bu diziler, Boolean türleri, char türleri, temsilciler, sınıflar, nesneler, dizeleri ve yapıları mareşal hakkında ayrıntılı bilgi sunar.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5eaf8-107">Genel türlerin mareşalliği desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="5eaf8-108">Daha fazla bilgi için bkz: [Genel Türleri Kullanarak Ara Çalışma.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5eaf8-108">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="5eaf8-109">Interop mareşal ile bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="5eaf8-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="5eaf8-110">Interop mareşal her zaman yönetilmeyen kod tarafından ayrılan belleği serbest etmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="5eaf8-111">Bu davranış, COM bellek yönetimi kurallarına uygundur, ancak yerel C++'ı yöneten kurallardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="5eaf8-112">Platform çağrısı nı kullanırken yerel C++ davranışını (bellek serbestiyeti yok) tahmin ederseniz, bu da işaretçiler için belleği otomatik olarak serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="5eaf8-113">Örneğin, bir C++ DLL'den aşağıdaki yönetilmeyen yöntemi çağırmak otomatik olarak herhangi bir belleği serbest bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="5eaf8-114">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="5eaf8-114">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="5eaf8-115">Ancak, yöntemi bir platform çağrısı prototipi olarak tanımlarsanız, <xref:System.String> her **BSTR** türünü bir türle değiştirin ve ortak dil çalışma zamanı denemelerini iki kez ücretsiz `MethodOne` `b` olarak arayın.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="5eaf8-116">**String** türleri yerine türleri kullanarak <xref:System.IntPtr> mareşal davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="5eaf8-117">Çalışma süresi her zaman ücretsiz bellek **için CoTaskMemFree** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="5eaf8-118">Çalıştığınız bellek **CoTaskMemAlloc** yöntemiyle ayrılmadıysa, bir **IntPtr** kullanmalı ve uygun yöntemi kullanarak belleği el ile serbest bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="5eaf8-119">Benzer şekilde, kernel32.dll'den **GetCommandLine** işlevini kullanırken olduğu gibi belleğin asla serbest bırakılmaması gereken durumlarda otomatik bellek serbest bırakMasını önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="5eaf8-120">Belleği el ile serbest etme yle ilgili ayrıntılar için [Arabellek Örneği'ne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-120">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="5eaf8-121">Sınıflar için varsayılan mareşalleme</span><span class="sxs-lookup"><span data-stu-id="5eaf8-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="5eaf8-122">Sınıflar yalnızca COM interop tarafından marshaled olabilir ve her zaman arayüz olarak marshaled vardır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="5eaf8-123">Bazı durumlarda sınıfı mareşallemek için kullanılan arabirim sınıf arabirimi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="5eaf8-124">Seçtiğiniz bir arabirimile sınıf arabirimini geçersiz kılma hakkında bilgi [için](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)bkz.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="5eaf8-125">Sınıfları COM'a Geçirme</span><span class="sxs-lookup"><span data-stu-id="5eaf8-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="5eaf8-126">Yönetilen bir sınıf COM'a geçirildiğinde, interop mareşal otomatik olarak bir COM proxy ile sınıfı sarar ve proxy tarafından üretilen sınıf arabirimini COM yöntemi çağrısına geçirir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="5eaf8-127">Proxy daha sonra sınıf arabirimindeki tüm çağrıları yönetilen nesneye geri verir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="5eaf8-128">Proxy, sınıf tarafından açıkça uygulanmayan diğer arabirimleri de ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="5eaf8-129">Proxy, sınıf adına **IUnknown** ve **IDispatch** gibi arabirimleri otomatik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="5eaf8-130">Sınıfları .NET Koduna Geçirme</span><span class="sxs-lookup"><span data-stu-id="5eaf8-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="5eaf8-131">Ortak sınıflar genellikle COM'da yöntem bağımsız değişkenleri olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="5eaf8-132">Bunun yerine, varsayılan arabirim genellikle ortak sınıfın yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="5eaf8-133">Bir arabirim yönetilen koda geçirildiğinde, interop mareşal doğru sarıcı ile arabirimi sarma ve yönetilen yönteme sarıcı geçmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="5eaf8-134">Hangi sarıcının kullanılacağını belirlemek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="5eaf8-135">Com nesnesinin her örneğinde, nesne nin kaç arabirimi uygularsa uygulanın, tek, benzersiz bir sarıcı bulunur.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="5eaf8-136">Örneğin, beş farklı arabirimi uygulayan tek bir COM nesnesi yalnızca bir sarıcıya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="5eaf8-137">Aynı sarıcı beş arabirimi de ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="5eaf8-138">COM nesnesinin iki örneği oluşturulursa, sarıcının iki örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="5eaf8-139">Sarılayıcının ömrü boyunca aynı türü koruyabilmesi için, interop mareşalinin nesne tarafından açığa çıkarılan bir arabirim mareşalden ilk kez doğru sarılayıcıyı tanımlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="5eaf8-140">Mareşal, nesnenin uyguladığı arabirimlerden birine bakarak nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="5eaf8-141">Örneğin, mareşal, yönetilen koda geçirilen arabirimi sarmak için sınıf sarıcının kullanılması gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="5eaf8-142">Arabirim mareşalden ilk geçirildiğinde, mareşal arabirimin bilinen bir nesneden gelip gelmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="5eaf8-143">Bu denetim iki durumda oluşur:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-143">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="5eaf8-144">Bir arabirim, başka bir yerde COM'a geçirilen başka bir yönetilen nesne tarafından uygulanMaktadır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="5eaf8-145">Marshaler, yönetilen nesneler tarafından maruz kalan arabirimleri kolayca tanımlayabilir ve arabirimi uygulamayı sağlayan yönetilen nesneyle eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="5eaf8-146">Yönetilen nesne daha sonra yönteme geçirilir ve sarıcı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="5eaf8-147">Zaten sarılmış bir nesne arabirimi uyguluyor.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="5eaf8-148">Bu durumda olup olmadığını belirlemek için, mareşal **nesneyi IUnknown** arabirimi için sorgular ve döndürülen arabirimi zaten sarılmış olan diğer nesnelerin arabirimlerinin karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="5eaf8-149">Arabirim başka bir sarıcıyla aynıysa, nesneler aynı kimliğe sahiptir ve varolan sarıcı yönteme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="5eaf8-150">Bir arabirim bilinen bir nesneden değilse, mareşal aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="5eaf8-151">Mareşal, **iProvideClassInfo2** arabirimi için nesneyi sorgular.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="5eaf8-152">Sağlanırsa, mareşal clsid **iProvideClassInfo2.GetGUID** gelen arayüz sağlayan coclass tanımlamak için döndürülür kullanır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="5eaf8-153">CLSID ile, montaj daha önce kaydedilmişse, mareşal ambalajı kayıt defterinden bulabilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="5eaf8-154">Mareşal, **IProvideClassInfo** arabiriminin arabirimini sorgular.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="5eaf8-155">Sağlanırsa, mareşal **iProvideClassInfo.GetClassinfo** gelen **iTypeInfo** sınıfının CLSID arayüzü açığa belirlemek için döndürülür kullanır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="5eaf8-156">Mareşal, sarıcının meta verilerini bulmak için CLSID'yi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="5eaf8-157">Mareşal hala sınıfı tanımlayamıyorsa, **system.__ComObject**adlı genel bir sarmalayıcı sınıfı ile arabirimi sarar.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="5eaf8-158">Temsilciler için varsayılan mareşalleme</span><span class="sxs-lookup"><span data-stu-id="5eaf8-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="5eaf8-159">Yönetilen bir temsilci, arama mekanizmasına bağlı olarak COM arabirimi veya işlev işaretçisi olarak sıralanır:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="5eaf8-160">Platform çağrısı için, bir temsilci varsayılan olarak yönetilmeyen bir işlev işaretçisi olarak marshaled.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="5eaf8-161">COM interop için, varsayılan olarak _Delegate **tür** com arabirimi olarak bir temsilci marshaled.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="5eaf8-162">**_Delegate** arabirimi Mscorlib.tlb türü kitaplığında <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> tanımlanır ve temsilcinin başvuruladığı yöntemi aramanızı sağlayan yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="5eaf8-163">Aşağıdaki tablo, yönetilen temsilci veri türü için mareşal seçenekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="5eaf8-164">Öznitelik, <xref:System.Runtime.InteropServices.MarshalAsAttribute> mareşal temsilcilerine birkaç <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="5eaf8-165">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="5eaf8-165">Enumeration type</span></span>|<span data-ttu-id="5eaf8-166">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="5eaf8-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="5eaf8-167">**YönetilmeyenType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="5eaf8-168">Yönetilmeyen bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="5eaf8-169">**YönetilmeyenType.Interface**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="5eaf8-170">Mscorlib.tlb'de tanımlandığı gibi tip **_Delegate**arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="5eaf8-171">Yöntemlerinin COM türü kitaplığına `DelegateTestInterface` dışa aktarıldığı aşağıdaki örnek kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="5eaf8-172">Yalnızca **ref** (veya **ByRef)** anahtar sözcüğüyle işaretlenmiş temsilcilerin Giriş/Çıkış parametreleri olarak geçirildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="5eaf8-173">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="5eaf8-173">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="5eaf8-174">Diğer yönetilmeyen işlev işaretçisi de reference'dan arındırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="5eaf8-175">Bu örnekte, iki temsilci olarak <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>marshaled olduğunda , `int` sonuç bir `int`ve bir işaretçi .</span><span class="sxs-lookup"><span data-stu-id="5eaf8-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="5eaf8-176">Temsilci türleri marshaled olduğundan, `int` burada bellekte temsilcinin adresi olan bir boşluk için`void*`bir işaretçi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="5eaf8-177">Başka bir deyişle, burada işlev işaretçisinin boyutunu `int` temsil ettiği için, bu sonuç 32 bit Windows sistemlerine özgüdür.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="5eaf8-178">İşlemeyen kod tarafından tutulan yönetilen bir temsilciye işlev işaretçisine yapılan başvuru, ortak dil çalışma zamanının yönetilen nesne üzerinde çöp toplama gerçekleştirmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="5eaf8-179">`cb` Örneğin, `SetChangeHandler` yönteme aktarılan nesneye yapılan başvuru `cb` `Test` yöntemin ömrü dışında canlı tutmadığından, aşağıdaki kod yanlıştır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="5eaf8-180">`cb` Nesne çöp toplandıktan sonra, geçirilen `SetChangeHandler` işlev işaretçisi artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="5eaf8-181">Beklenmeyen çöp toplamayı telafi etmek için, `cb` arayan, yönetilmeyen işlev işaretçisi kullanıldığı sürece nesnenin canlı tutulduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="5eaf8-182">İsteğe bağlı olarak, aşağıdaki örnekte görüldüğü gibi, işlev işaretçisi artık gerekli olmadığında, yönetilmeyen kodun yönetilen kodu bildirmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="5eaf8-183">Değer türleri için varsayılan mareşalleme</span><span class="sxs-lookup"><span data-stu-id="5eaf8-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="5eaf8-184">Tamsayılar ve kayan nokta sayıları gibi çoğu değer türü [blittable](blittable-and-non-blittable-types.md) ve mareşallik gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="5eaf8-185">Diğer [blittable olmayan](blittable-and-non-blittable-types.md) türleri yönetilen ve yönetilmeyen bellekfarklı gösterimleri var ve mareşalgerektirir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="5eaf8-186">Yine de diğer türler, işlem ler arası sınır boyunca açık biçimlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="5eaf8-187">Bu bölümde aşağıdaki biçimlendirilmiş değer türleri hakkında bilgi verilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-187">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="5eaf8-188">Platform Çağırmada Kullanılan Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="5eaf8-188">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="5eaf8-189">COM Interop'ta Kullanılan Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="5eaf8-189">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="5eaf8-190">Biçimlendirilmiş türleri açıklamaya ek olarak, bu konu olağandışı mareşal davranışı olan [Sistem Değer Türlerini](#system-value-types) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-190">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="5eaf8-191">Biçimlendirilmiş tür, bellekteki üyelerinin düzenini açıkça denetleyen bilgiler içeren karmaşık bir türdür.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="5eaf8-192">Üye düzeni bilgileri öznitelik <xref:System.Runtime.InteropServices.StructLayoutAttribute> kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="5eaf8-193">Düzen aşağıdaki <xref:System.Runtime.InteropServices.LayoutKind> numaralandırma değerlerinden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="5eaf8-194">**LayoutKind.Auto**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-194">**LayoutKind.Auto**</span></span>  
  
     <span data-ttu-id="5eaf8-195">Ortak dil çalışma zamanının, türdeki üyeleri verimlilik için yeniden sıralamak için ücretsiz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="5eaf8-196">Ancak, bir değer türü yönetilmeyen koda geçirildiğinde, üyelerin düzeni tahmin edilebilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="5eaf8-197">Böyle bir yapıyı mareşalleme girişimi otomatik olarak bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="5eaf8-198">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="5eaf8-199">Türün üyelerinin yönetilen tür tanımında göründükleri aynı sırada yönetilmeyen bellekte ortaya konacaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="5eaf8-200">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="5eaf8-201">Üyelerin her alanla <xref:System.Runtime.InteropServices.FieldOffsetAttribute> birlikte verilen alana göre yerleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="5eaf8-202">Platform Çağırmada Kullanılan Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="5eaf8-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="5eaf8-203">Aşağıdaki örnekte `Point` ve `Rect` türleri **StructLayoutAttribute**kullanarak üye düzeni bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="5eaf8-204">Yönetilmeyen koda marshaled zaman, bu biçimlendirilmiş türleri C tarzı yapılar olarak marshaled.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="5eaf8-205">Bu, yapı bağımsız değişkenleri olan yönetilmeyen bir API'yi çağırmanın kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="5eaf8-206">Örneğin, ve `POINT` `RECT` yapıları Aşağıdaki gibi Microsoft Windows API **PtInRect** işlevine geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="5eaf8-207">Yapıları aşağıdaki platform çağırma tanımını kullanarak geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-207">You can pass structures using the following platform invoke definition:</span></span>  
  
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
  
 <span data-ttu-id="5eaf8-208">Yönetilmeyen API bir işaretçi `Rect` `RECT` işlevine geçirilecek bekliyor, çünkü değer türü başvuru tarafından geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="5eaf8-209">Yönetilmeyen API yığında `Point` `POINT` geçirilmeyi beklediğinden, değer türü değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="5eaf8-210">Bu ince fark çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-210">This subtle difference is very important.</span></span> <span data-ttu-id="5eaf8-211">Başvurular yönetilmeyen koda işaretçi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="5eaf8-212">Değerler yığındaki yönetilmeyen koda aktarılır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5eaf8-213">Biçimlendirilmiş bir tür yapı olarak sıralandığında, yalnızca tür içindeki alanlara erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="5eaf8-214">Türde yöntemler, özellikler veya olaylar varsa, bunlara yönetilmeyen koddan erişilemezler.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="5eaf8-215">Sınıflar, sabit üye düzenine sahip olmaları koşuluyla, yönetilmeyen koda C stili yapılar olarak da marshaled olabilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="5eaf8-216">Bir sınıfın üye düzeni bilgileri de <xref:System.Runtime.InteropServices.StructLayoutAttribute> öznitelik ile sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="5eaf8-217">Sabit düzene sahip değer türleri ile sabit düzene sahip sınıflar arasındaki temel fark, bunların yönetilmeyen koda marshaled yoludur.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="5eaf8-218">Değer türleri değere göre geçirilir (yığında) ve dolayısıyla callee tarafından türün üyelerine yapılan değişiklikler arayan tarafından görülmez.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="5eaf8-219">Başvuru türleri başvuru ile geçirilir (yığında türe bir başvuru geçirilir); sonuç olarak, callee tarafından bir türün blittable türünde üyeler için yapılan tüm değişiklikler arayan tarafından görülür.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5eaf8-220">Bir başvuru türünde blittable olmayan türlerin üyeleri varsa, dönüştürme iki kez gereklidir: ilk kez bir bağımsız değişken yönetilmeyen tarafa geçirildiğinde ve ikinci kez çağrıdan dönüşte.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="5eaf8-221">Eklenen bu ek yükü nedeniyle, arayan callee tarafından yapılan değişiklikleri görmek istiyorsa, In/Out parametreleri açıkça bir bağımsız değişkene uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="5eaf8-222">Aşağıdaki örnekte, `SystemTime` sınıf sıralı üye düzeni vardır ve Windows API **GetSystemTime** işlevine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="5eaf8-223">**GetSystemTime** işlevi aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="5eaf8-224">**GetSystemTime** için eşdeğer platform çağırma tanımı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5eaf8-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
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
  
 <span data-ttu-id="5eaf8-225">`SystemTime` Bir sınıf değil, bir değer türü `SystemTime` olduğundan bağımsız değişkenin başvuru bağımsız değişkeni olarak yazıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="5eaf8-226">Değer türlerinden farklı olarak, sınıflar her zaman başvuru ile geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="5eaf8-227">Aşağıdaki kod örneği, `Point` .. `SetXY`</span><span class="sxs-lookup"><span data-stu-id="5eaf8-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="5eaf8-228">Tür sıralı düzene sahip olduğundan, yönetilmeyen koda geçirilebilir ve bir yapı olarak marshaled.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="5eaf8-229">Ancak, `SetXY` nesne başvuru tarafından geçirilse bile, üye yönetilmeyen koddan çağrılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="5eaf8-230">COM Interop'ta Kullanılan Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="5eaf8-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="5eaf8-231">Biçimlendirilmiş türler com interop yöntemi çağrılarına da aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="5eaf8-232">Aslında, bir tür kitaplığına dışa aktarıldığında, değer türleri otomatik olarak yapılara dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="5eaf8-233">Aşağıdaki örnekte görüldüğü `Point` gibi, değer türü bir tür tanımı `Point`(typedef) adı ile olur.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="5eaf8-234">Tür kitaplığındaki `Point` değer türüne yapılan tüm başvurular `Point` typedef ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="5eaf8-235">**Tür kitaplığı gösterimi**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-235">**Type library representation**</span></span>  
  
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
  
 <span data-ttu-id="5eaf8-236">Değerleri ve platform çağrı çağrılarına yapılan başvuruları mareşallemek için kullanılan aynı kurallar, COM arabirimleri aracılığıyla gezinirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="5eaf8-237">Örneğin, `Point` değer türünün bir örneği .NET Framework'den COM'a geçirildiğinde, değere göre `Point` geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="5eaf8-238">`Point` Değer türü başvuru yla geçirilirse, `Point` a işaretçisi yığına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="5eaf8-239">Interop mareşal her iki yönde de daha yüksek yönlendirme **(Nokta)** \* \*düzeylerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5eaf8-240"><xref:System.Runtime.InteropServices.LayoutKind> Dışa aktarılan tür kitaplığı açık bir düzeni ifade edemediğinden, numaralandırma değeri **Explicit** olarak ayarlanmış yapılar COM interop'ta kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="5eaf8-241">Sistem Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="5eaf8-241">System Value Types</span></span>  
 <span data-ttu-id="5eaf8-242">Ad <xref:System> alanı, çalışma zamanı ilkel türlerinin kutulanmış biçimini temsil eden birkaç değer türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="5eaf8-243">Örneğin, değer türü <xref:System.Int32?displayProperty=nameWithType> yapısı **ELEMENT_TYPE_I4**kutulu biçimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="5eaf8-244">Bu türleri, diğer biçimlendirilmiş türler gibi yapı olarak sıralamayerine, kutuladıkları ilkel türlerle aynı şekilde sıralarsınız.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="5eaf8-245">**System.Int32** bu nedenle ELEMENT_TYPE_I4 **yerine** tip **uzun**tek bir üyesi içeren bir yapı olarak marshaled olduğunu.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="5eaf8-246">Aşağıdaki tablo, **Sistem** ad alanında ilkel türlerin kutulu gösterimleri olan değer türlerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="5eaf8-247">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="5eaf8-247">System value type</span></span>|<span data-ttu-id="5eaf8-248">Eleman türü</span><span class="sxs-lookup"><span data-stu-id="5eaf8-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="5eaf8-264">**Sistem** ad alanındaki diğer bazı değer türleri farklı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="5eaf8-265">Yönetilmeyen kod zaten bu tür için iyi kurulmuş biçimleri olduğundan, mareşal bunları mareşaliçin özel kurallar vardır.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="5eaf8-266">Aşağıdaki **tabloda, Sistem** ad alanında özel değer türlerinin yanı sıra, yürütülemeyen türler listelenir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="5eaf8-267">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="5eaf8-267">System value type</span></span>|<span data-ttu-id="5eaf8-268">IDL türü</span><span class="sxs-lookup"><span data-stu-id="5eaf8-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-269">**Tarih**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-270">**On -da -lık**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-271">**Guıd**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="5eaf8-272">**Ole_color**</span><span class="sxs-lookup"><span data-stu-id="5eaf8-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="5eaf8-273">Aşağıdaki kod, Stdole2 türü kitaplığında yönetilmeyen **DATE**, **GUID**, **DECIMAL**ve **OLE_COLOR** türlerinin tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="5eaf8-274">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="5eaf8-274">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="5eaf8-275">Aşağıdaki kod, yönetilen `IValueTypes` arabirimdeki karşılık gelen tanımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="5eaf8-276">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="5eaf8-276">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="5eaf8-277">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5eaf8-277">See also</span></span>

- [<span data-ttu-id="5eaf8-278">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="5eaf8-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="5eaf8-279">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="5eaf8-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="5eaf8-280">Diziler için Varsayılan Sıralama</span><span class="sxs-lookup"><span data-stu-id="5eaf8-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="5eaf8-281">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="5eaf8-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="5eaf8-282">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="5eaf8-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
