---
title: Varsayılan Sıralama Davranışı
description: .NET ' te varsayılan sıralama davranışını öğrenin. Birlikte çalışabilirlik sıralaması ile bellek yönetimini gözden geçirin ve sınıflar, temsilciler ve değer türleri için varsayılan sıralama bölümüne bakın.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: f2a508b87d2f4a9ad92bc0f27fc44d74d8e916d3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555282"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="47e35-104">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="47e35-104">Default Marshaling Behavior</span></span>
<span data-ttu-id="47e35-105">Birlikte çalışabilirlik sıralaması, yöntem parametreleriyle ilişkili verilerin yönetilen ve yönetilmeyen bellek arasında geçerken nasıl davranacağını dikte eden kurallar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="47e35-105">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="47e35-106">Bu yerleşik kurallar, verileri veri türü dönüşümleri olarak sıralama, bir çağrılan verilerin kendisine geçirilen verileri değiştirip çağıramayacağını ve bu değişiklikleri arayana döndürmesini ve bu değişiklikleri, Sıralayıcı 'nın performans iyileştirmeleri sağladığı koşullarda değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="47e35-106">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="47e35-107">Bu bölüm, birlikte çalışma sıralama hizmetinin varsayılan davranış özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47e35-107">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="47e35-108">Dizileri, Boole türlerini, karakter türlerini, temsilcileri, sınıfları, nesneleri, dizeleri ve yapıları hazırlama hakkında ayrıntılı bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="47e35-108">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47e35-109">Genel türlerin sıralaması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="47e35-109">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="47e35-110">Daha fazla bilgi için bkz. [Genel türler kullanılarak birlikte çalışma](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="47e35-110">For more information see, [Interoperating Using Generic Types](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="47e35-111">Birlikte çalışma sıralayıcısı ile bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="47e35-111">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="47e35-112">Birlikte çalışma sıralayıcısı, her zaman yönetilmeyen kod tarafından ayrılan belleği serbest bırakma girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="47e35-112">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="47e35-113">Bu davranış, COM bellek yönetimi kurallarına uyar, ancak yerel C++ ' ı yöneten kurallardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="47e35-113">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="47e35-114">Platform çağırma kullanılırken yerel C++ davranışını (bellek boşaltma yok) tahmin ediyorsanız karışıklığa neden olabilir. Bu, işaretçiler için belleği otomatik olarak boşaltır.</span><span class="sxs-lookup"><span data-stu-id="47e35-114">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="47e35-115">Örneğin, bir C++ DLL 'den aşağıdaki yönetilmeyen yöntemi çağırmak herhangi bir belleği otomatik olarak serbest vermez.</span><span class="sxs-lookup"><span data-stu-id="47e35-115">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="47e35-116">Yönetilmeyen imza</span><span class="sxs-lookup"><span data-stu-id="47e35-116">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="47e35-117">Ancak, yöntemi bir platform çağırma prototipi olarak tanımlarsanız, her **BSTR** türünü bir tür ile değiştirin <xref:System.String> ve çağırın `MethodOne` , ortak dil çalışma zamanı iki kez ücretsiz olarak çalışır `b` .</span><span class="sxs-lookup"><span data-stu-id="47e35-117">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="47e35-118">Sıralama davranışını <xref:System.IntPtr> **dize** türleri yerine türler kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47e35-118">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="47e35-119">Çalışma zamanı, belleği boşaltmak için her zaman **CoTaskMemFree** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="47e35-119">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="47e35-120">Çalıştığınız bellek **CoTaskMemAlloc** yöntemiyle ayrıldıysa, bir **IntPtr** kullanmanız ve uygun yöntemi kullanarak belleği el ile boşaltmalısınız.</span><span class="sxs-lookup"><span data-stu-id="47e35-120">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="47e35-121">Benzer şekilde, çekirdek belleğine bir işaretçi döndüren Kernel32.dll **GetCommandLine** işlevini kullanırken, belleğin asla boşaltılmaması gereken durumlarda otomatik bellek boşaltmasını önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47e35-121">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="47e35-122">Belleği el ile boşaltma hakkında ayrıntılı bilgi için bkz. [arabellekler örneği](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="47e35-122">For details on manually freeing memory, see the [Buffers Sample](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="47e35-123">Sınıflar için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="47e35-123">Default marshaling for classes</span></span>  
 <span data-ttu-id="47e35-124">Sınıflar yalnızca COM birlikte çalışabilirliğine göre sıralanabilir ve her zaman arabirim olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="47e35-124">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="47e35-125">Bazı durumlarda, sınıfı sıralamak için kullanılan arabirim sınıf arabirimi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="47e35-125">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="47e35-126">Sınıf arabirimini tercih ettiğiniz bir arabirimle geçersiz kılma hakkında daha fazla bilgi için bkz. [sınıf arabirimine giriş](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="47e35-126">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="47e35-127">Sınıfları COM 'a geçirme</span><span class="sxs-lookup"><span data-stu-id="47e35-127">Passing Classes to COM</span></span>  
 <span data-ttu-id="47e35-128">Yönetilen bir sınıf COM 'a geçirildiğinde, birlikte çalışma sıralayıcısı otomatik olarak sınıfı bir COM proxy 'si ile sarmalanmış ve proxy tarafından üretilen sınıf arabirimini COM yöntem çağrısına geçirir.</span><span class="sxs-lookup"><span data-stu-id="47e35-128">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="47e35-129">Ardından ara sunucu, sınıf arabirimindeki tüm çağrıları yönetilen nesneye yeniden devreder.</span><span class="sxs-lookup"><span data-stu-id="47e35-129">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="47e35-130">Proxy Ayrıca, sınıfı tarafından açıkça uygulanmayan diğer arabirimleri de kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="47e35-130">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="47e35-131">Proxy, sınıf adına **IUnknown** ve **IDispatch** gibi arabirimleri otomatik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="47e35-131">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="47e35-132">Sınıfları .NET koduna geçirme</span><span class="sxs-lookup"><span data-stu-id="47e35-132">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="47e35-133">Ortak sınıflar genellikle COM 'da Yöntem bağımsız değişkenleri olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="47e35-133">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="47e35-134">Bunun yerine, varsayılan bir arabirim genellikle coclass 'ın yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-134">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="47e35-135">Bir arabirim yönetilen koda geçirildiğinde, birlikte çalışma sıralayıcısı, arabirimin doğru sarmalayıcı ile sarmalanması ve sarmalayıcı yönetilen yönteme geçirilmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="47e35-135">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="47e35-136">Hangi sarmalayıcı kullanacağınızı belirlemek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-136">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="47e35-137">Bir COM nesnesinin her örneği, nesnenin kaç arabirim uyguladığını fark etmeksizin tek ve benzersiz bir sarmalayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="47e35-137">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="47e35-138">Örneğin, beş farklı arabirimi uygulayan tek bir COM nesnesi yalnızca bir sarmalayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="47e35-138">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="47e35-139">Aynı sarmalayıcı beş arabirimi de kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="47e35-139">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="47e35-140">COM nesnesinin iki örneği oluşturulursa, sarmalayıcının iki örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="47e35-140">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="47e35-141">Sarmalayıcının ömrü boyunca aynı türü koruabilmesi için, nesne tarafından kullanıma sunulan bir arabirim Sıralayıcı üzerinden geçirildiğinde, birlikte çalışma sıralayıcısı doğru sarmalayıcı tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="47e35-141">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="47e35-142">Sıralayıcı nesnenin uyguladığı arayüzlerden birine bakarak nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47e35-142">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="47e35-143">Örneğin Sıralayıcı, sınıf sarmalayıcının yönetilen koda geçirilen arabirimi sarmalamak için kullanılması gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="47e35-143">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="47e35-144">Arabirim Sıralayıcı tarafından ilk kez geçirildiğinde Sıralayıcı, arabirimin bilinen bir nesneden geliyor olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="47e35-144">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="47e35-145">Bu denetim iki durumda gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="47e35-145">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="47e35-146">Bir arabirim, COM 'a başka bir yerde geçirilmiş başka bir yönetilen nesne tarafından uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="47e35-146">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="47e35-147">Sıralayıcı yönetilen nesneler tarafından sunulan arabirimleri kolayca tanımlayabilir ve arabirimi, uygulamayı sağlayan yönetilen nesneyle eşleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-147">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="47e35-148">Yönetilen nesne daha sonra yönteme geçirilir ve sarmalayıcı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="47e35-148">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="47e35-149">Zaten sarmalanmış bir nesne arabirimini uygulama.</span><span class="sxs-lookup"><span data-stu-id="47e35-149">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="47e35-150">Bunun durum olup olmadığını anlamak için sıralayıcı, nesneyi **IUnknown** arabirimine sorgular ve döndürülen arabirimi zaten sarmalanmış diğer nesnelerin arabirimlerine karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="47e35-150">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="47e35-151">Arabirim, başka bir sarmalayıcı ile aynıysa, nesneler aynı kimliğe sahip olur ve varolan sarmalayıcı yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-151">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="47e35-152">Bir arabirim bilinen bir nesneden değilse Sıralayıcı şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="47e35-152">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="47e35-153">Sıralayıcı, **IProvideClassInfo2** arabirimi için nesneyi sorgular.</span><span class="sxs-lookup"><span data-stu-id="47e35-153">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="47e35-154">Sağlanmışsa, Sıralayıcı, arabirimi sağlayan coclass 'ı tanımlamak için **IProvideClassInfo2. GetGUID** ÖĞESINDEN döndürülen CLSID 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="47e35-154">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="47e35-155">CLSID ile, derleme daha önce kaydedilmişse, Sıralayıcı kayıt defterinden sarmalayıcı bulabilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-155">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="47e35-156">Sıralayıcı, **IProvideClassInfo** arabirimi için arabirimi sorgular.</span><span class="sxs-lookup"><span data-stu-id="47e35-156">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="47e35-157">Belirtilmişse, Sıralayıcı, arabirimi kullanıma sunmadan sınıfın CLSID 'sini belirlemede **IProvideClassInfo. GetClassInfo** öğesinden döndürülen **ITypeInfo bilgisini** kullanır.</span><span class="sxs-lookup"><span data-stu-id="47e35-157">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="47e35-158">Sıralayıcı, sarmalayıcının meta verilerini bulmak için CLSID 'yi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-158">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="47e35-159">Sıralayıcı hala sınıfı tanımlayamıyor, arabirimi **System. __ComObject**adlı bir genel sarmalayıcı sınıfı ile sarmalanmış hale gelir.</span><span class="sxs-lookup"><span data-stu-id="47e35-159">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="47e35-160">Temsilciler için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="47e35-160">Default marshaling for delegates</span></span>  
 <span data-ttu-id="47e35-161">Yönetilen bir temsilci, çağırma mekanizmasına bağlı olarak bir COM arabirimi veya bir işlev işaretçisi olarak sıralanır:</span><span class="sxs-lookup"><span data-stu-id="47e35-161">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="47e35-162">Platform çağırma için bir temsilci varsayılan olarak yönetilmeyen bir işlev işaretçisi olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="47e35-162">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="47e35-163">COM birlikte çalışması için bir temsilci, varsayılan olarak **_Delegate** türünde bir com arabirimi olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="47e35-163">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="47e35-164">**_Delegate** arabirimi mscorlib. tlb tür kitaplığında tanımlanmıştır ve <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> temsilcinin başvurduğu yöntemi çağırabilmenizi sağlayan yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="47e35-164">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="47e35-165">Aşağıdaki tabloda, yönetilen temsilci veri türü için sıralama seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47e35-165">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="47e35-166"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği, <xref:System.Runtime.InteropServices.UnmanagedType> temsilcileri sıralamak için birkaç numaralandırma değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="47e35-166">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="47e35-167">Sabit listesi türü</span><span class="sxs-lookup"><span data-stu-id="47e35-167">Enumeration type</span></span>|<span data-ttu-id="47e35-168">Yönetilmeyen biçimin açıklaması</span><span class="sxs-lookup"><span data-stu-id="47e35-168">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="47e35-169">**UnmanagedType. FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="47e35-169">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="47e35-170">Yönetilmeyen bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="47e35-170">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="47e35-171">**UnmanagedType. Interface**</span><span class="sxs-lookup"><span data-stu-id="47e35-171">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="47e35-172">Mscorlib. tlb ' de tanımlandığı şekilde **_Delegate**türünde bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="47e35-172">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="47e35-173">Yöntemlerinin `DelegateTestInterface` BIR com tür kitaplığına aktarılması için aşağıdaki örnek kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="47e35-173">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="47e35-174">Yalnızca **ref** (veya **ByRef**) anahtar sözcüğüyle Işaretlenen temsilcilerin ın/out parametrelerine geçtiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47e35-174">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="47e35-175">Tür kitaplığı temsili</span><span class="sxs-lookup"><span data-stu-id="47e35-175">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="47e35-176">Bir işlev işaretçisine, diğer yönetilmeyen işlev işaretçilerine başvurulanlar gibi başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47e35-176">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="47e35-177">Bu örnekte, iki temsilci olarak sıralandığınızda <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType> , sonuç bir `int` ve bir işaretçisidir `int` .</span><span class="sxs-lookup"><span data-stu-id="47e35-177">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="47e35-178">Temsilci türleri sıralanmakta olduğundan, `int` `void*` Bu, bellekteki temsilcinin adresi olan void () için bir işaretçi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="47e35-178">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="47e35-179">Diğer bir deyişle, bu sonuç 32 bitlik Windows sistemlerine özgüdür, bu nedenle `int` işlev işaretçisinin boyutunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="47e35-179">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="47e35-180">Yönetilmeyen kod tarafından tutulan yönetilen bir temsilciye yönelik işlev işaretçisine yönelik bir başvuru, ortak dil çalışma zamanının yönetilen nesnede çöp toplama gerçekleştirmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="47e35-180">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="47e35-181">Örneğin, `cb` yöntemine geçirilen nesneye yapılan başvuru, `SetChangeHandler` `cb` yöntemin ömrünün ötesinde etkin olmadığından, aşağıdaki kod yanlış `Test` .</span><span class="sxs-lookup"><span data-stu-id="47e35-181">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="47e35-182">`cb`Nesne çöp topladıktan sonra, geçirilen işlev işaretçisi `SetChangeHandler` artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="47e35-182">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="47e35-183">Beklenmedik atık toplamayı dengelemek için çağıran, `cb` yönetilmeyen işlev işaretçisi kullanımda olduğu sürece nesnenin canlı tutulduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47e35-183">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="47e35-184">İsteğe bağlı olarak, aşağıdaki örnekte gösterildiği gibi, işlev işaretçisine artık ihtiyaç duyulmadığında, yönetilmeyen kodun yönetilen koda bildirilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47e35-184">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="47e35-185">Değer türleri için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="47e35-185">Default marshaling for value types</span></span>  
 <span data-ttu-id="47e35-186">Tamsayılar ve kayan nokta numaraları gibi çoğu değer türleri [blittable](blittable-and-non-blittable-types.md) ve sıralama gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="47e35-186">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="47e35-187">Diğer [blittable dışı](blittable-and-non-blittable-types.md) türler yönetilen ve yönetilmeyen bellekte benzer temsiller ve sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="47e35-187">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="47e35-188">Hala diğer türler, birlikte çalışma sınırları genelinde açık biçimlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="47e35-188">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="47e35-189">Bu bölüm aşağıdaki biçimli değer türleri hakkında bilgi sağlar:</span><span class="sxs-lookup"><span data-stu-id="47e35-189">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="47e35-190">Platform çağırmada kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="47e35-190">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="47e35-191">COM birlikte çalışabilirliğine kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="47e35-191">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="47e35-192">Bu konuda, biçimlendirilen türlerin açıklanmasına ek olarak, olağan dışı sıralama davranışına sahip [Sistem değeri türleri](#system-value-types) tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47e35-192">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="47e35-193">Biçimlendirilen bir tür, içindeki üyelerinin doğrudan, bellekteki yerleşimini açıkça denetleyen bilgiler içeren karmaşık bir türdür.</span><span class="sxs-lookup"><span data-stu-id="47e35-193">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="47e35-194">Üye düzen bilgileri, özniteliği kullanılarak sağlanır <xref:System.Runtime.InteropServices.StructLayoutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="47e35-194">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="47e35-195">Düzen aşağıdaki <xref:System.Runtime.InteropServices.LayoutKind> sabit listesi değerlerinden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="47e35-195">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="47e35-196">**LayoutKind. Auto**</span><span class="sxs-lookup"><span data-stu-id="47e35-196">**LayoutKind.Auto**</span></span>  
  
     <span data-ttu-id="47e35-197">Ortak dil çalışma zamanının, verimlilik için tür üyelerini yeniden sıralamak için boş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="47e35-197">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="47e35-198">Ancak, bir değer türü yönetilmeyen koda geçirildiğinde, üyelerin düzeni öngörülebilir olur.</span><span class="sxs-lookup"><span data-stu-id="47e35-198">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="47e35-199">Böyle bir yapıyı sıralama girişimi özel duruma otomatik olarak neden olur.</span><span class="sxs-lookup"><span data-stu-id="47e35-199">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="47e35-200">**LayoutKind. Sequential**</span><span class="sxs-lookup"><span data-stu-id="47e35-200">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="47e35-201">Türün üyelerinin yönetilmeyen bellekte, yönetilen tür tanımında göründükleri sırada düzenleneceğini gösterir...</span><span class="sxs-lookup"><span data-stu-id="47e35-201">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="47e35-202">**LayoutKind. Explicit**</span><span class="sxs-lookup"><span data-stu-id="47e35-202">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="47e35-203">Üyelerin her alanla sağlanan öğesine göre düzenlendiğini gösterir <xref:System.Runtime.InteropServices.FieldOffsetAttribute> .</span><span class="sxs-lookup"><span data-stu-id="47e35-203">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="47e35-204">Platform çağırmada kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="47e35-204">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="47e35-205">Aşağıdaki örnekte, `Point` ve `Rect` türleri **StructLayoutAttribute**kullanarak üye düzen bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="47e35-205">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="47e35-206">Yönetilmeyen koda sıralandığınızda, bu biçimli türler C stili yapılar olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="47e35-206">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="47e35-207">Bu, yapı bağımsız değişkenlerine sahip yönetilmeyen bir API çağırmanın kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="47e35-207">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="47e35-208">Örneğin, `POINT` ve `RECT` yapıları MICROSOFT Windows API **ptinrect** işlevine aşağıdaki gibi geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="47e35-208">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="47e35-209">Aşağıdaki platform çağırma tanımını kullanarak yapıları geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="47e35-209">You can pass structures using the following platform invoke definition:</span></span>  
  
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
  
 <span data-ttu-id="47e35-210">`Rect`YÖNETILMEYEN API, işleve geçirilecek bir işaretçi beklediği için değer türü başvuruya göre geçirilmelidir `RECT` .</span><span class="sxs-lookup"><span data-stu-id="47e35-210">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="47e35-211">`Point`YÖNETILMEYEN API 'nin yığına geçirilmesini beklediği için değer türü değere göre geçirilir `POINT` .</span><span class="sxs-lookup"><span data-stu-id="47e35-211">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="47e35-212">Bu hafif fark çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="47e35-212">This subtle difference is very important.</span></span> <span data-ttu-id="47e35-213">Başvurular yönetilmeyen koda işaretçiler olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-213">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="47e35-214">Değerler yığında yönetilmeyen koda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-214">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47e35-215">Biçimlendirilen bir tür yapı olarak sıralanmışsa, yalnızca tür içindeki alanlara erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-215">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="47e35-216">Türün yöntemleri, özellikleri veya olayları varsa, bunlar yönetilmeyen koddan erişilmez.</span><span class="sxs-lookup"><span data-stu-id="47e35-216">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="47e35-217">Sınıflar, Ayrıca, sabit üye düzenine sahip olmaları şartıyla, yönetilmeyen koda C stili yapılar olarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-217">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="47e35-218">Bir sınıf için üye düzen bilgileri de özniteliğiyle birlikte sağlanır <xref:System.Runtime.InteropServices.StructLayoutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="47e35-218">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="47e35-219">Sabit düzen ve sınıflar ile değer türleri arasındaki temel fark, yönetilmeyen kod için sıralandıkları yoldur.</span><span class="sxs-lookup"><span data-stu-id="47e35-219">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="47e35-220">Değer türleri değeri (yığında) ile geçirilir ve sonuç olarak, aranan tarafından türün üyelerinde yapılan değişiklikler arayan tarafından görülmez.</span><span class="sxs-lookup"><span data-stu-id="47e35-220">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="47e35-221">Başvuru türleri başvuruya göre geçirilir (türe bir başvuru yığına geçirilir); Sonuç olarak, aranan tarafından bir türün blittable-Type üyelerinde yapılan tüm değişiklikler arayan tarafından görülür.</span><span class="sxs-lookup"><span data-stu-id="47e35-221">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47e35-222">Bir başvuru türünde blittable olmayan türlerde Üyeler varsa, dönüştürme iki kez gereklidir: bir bağımsız değişkenin yönetilmeyen tarafa geçirilmesi ve çağrıdan ikinci kez döndürülmesinin ilk zamanı.</span><span class="sxs-lookup"><span data-stu-id="47e35-222">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="47e35-223">Bu eklenen ek yük nedeniyle, çağıran tarafından yapılan değişiklikleri görmek istiyorsa, ın/out parametreleri açıkça bir bağımsız değişkene uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47e35-223">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="47e35-224">Aşağıdaki örnekte, `SystemTime` sınıfı sıralı üye düzenine sahiptir ve WINDOWS API **GetSystemTime** işlevine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-224">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="47e35-225">**GetSystemTime** işlevi şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="47e35-225">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="47e35-226">**GetSystemTime** için eşdeğer platform çağırma tanımı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="47e35-226">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
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
  
 <span data-ttu-id="47e35-227">`SystemTime`Bağımsız değişkenin bir başvuru bağımsız değişkeni olarak yazılmadığından `SystemTime` , bir değer türü değil bir sınıf olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="47e35-227">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="47e35-228">Değer türlerinin aksine, sınıflar her zaman başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-228">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="47e35-229">Aşağıdaki kod örneği, `Point` adlı bir yöntemi olan farklı bir sınıfı gösterir `SetXY` .</span><span class="sxs-lookup"><span data-stu-id="47e35-229">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="47e35-230">Türün sıralı düzeni olduğundan, yönetilmeyen koda geçirilebilir ve bir yapı olarak sıralanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-230">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="47e35-231">Ancak, `SetXY` nesne başvuru ile geçirilse bile, yönetilmeyen koddan üye çağrılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="47e35-231">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="47e35-232">COM birlikte çalışabilirliğine kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="47e35-232">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="47e35-233">Biçimlendirilen türler, COM birlikte çalışma yöntemi çağrılarına de geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-233">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="47e35-234">Aslında, bir tür kitaplığına aktarıldığında, değer türleri otomatik olarak yapılara dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="47e35-234">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="47e35-235">Aşağıdaki örnekte gösterildiği gibi, `Point` değer türü adıyla bir tür tanımı (typedef) olur `Point` .</span><span class="sxs-lookup"><span data-stu-id="47e35-235">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="47e35-236">`Point`Tür kitaplığının başka bir yerinde değer türüne yapılan tüm başvurular typedef ile değiştirilmiştir `Point` .</span><span class="sxs-lookup"><span data-stu-id="47e35-236">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="47e35-237">**Tür kitaplığı temsili**</span><span class="sxs-lookup"><span data-stu-id="47e35-237">**Type library representation**</span></span>  
  
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
  
 <span data-ttu-id="47e35-238">Değerleri ve platform çağırma çağrılarına başvuruları sıralamak için kullanılan kurallar, COM arabirimleri üzerinden sıralama yapılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47e35-238">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="47e35-239">Örneğin, `Point` değer türünün bir örneği .NET Framework com 'a geçirildiğinde, `Point` değeri tarafından geçirilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-239">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="47e35-240">`Point`Değer türü başvuruya göre geçirilirse, yığına bir işaretçisi `Point` geçirilir.</span><span class="sxs-lookup"><span data-stu-id="47e35-240">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="47e35-241">Birlikte çalışma sıralayıcısı,**Point** \* \* iki yönde de daha yüksek yöneltme (nokta) düzeylerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="47e35-241">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47e35-242"><xref:System.Runtime.InteropServices.LayoutKind>Sabit listesi değeri **Açık** olarak ayarlanmış olan yapılar, içe aktarılmış tür kitaplığı açık bir düzen Ifade ettiğinden, com birlikte çalışma içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="47e35-242">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="47e35-243">Sistem değer türleri</span><span class="sxs-lookup"><span data-stu-id="47e35-243">System Value Types</span></span>  
 <span data-ttu-id="47e35-244"><xref:System>Ad alanı, çalışma zamanı temel türlerinin paketlenmiş formunu temsil eden çeşitli değer türlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="47e35-244">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="47e35-245">Örneğin, değer türü yapısı, <xref:System.Int32?displayProperty=nameWithType> **ELEMENT_TYPE_I4**kutulanmış biçimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="47e35-245">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="47e35-246">Bu türleri yapılar olarak sıralamak yerine, diğer biçimlendirilen türler olduğu gibi, bunları kendi temel türleriyle aynı şekilde sıralamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47e35-246">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="47e35-247">Bu nedenle **System. Int32** , **Long**türünde tek bir üye içeren bir yapı olarak değil **ELEMENT_TYPE_I4** olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="47e35-247">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="47e35-248">Aşağıdaki tablo, temel türlerin kutulanmış temsilleri olan **sistem** ad alanındaki değer türlerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="47e35-248">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="47e35-249">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="47e35-249">System value type</span></span>|<span data-ttu-id="47e35-250">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="47e35-250">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="47e35-251">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="47e35-251">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="47e35-252">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="47e35-252">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="47e35-253">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="47e35-253">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="47e35-254">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="47e35-254">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="47e35-255">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="47e35-255">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="47e35-256">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="47e35-256">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="47e35-257">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="47e35-257">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="47e35-258">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="47e35-258">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="47e35-259">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="47e35-259">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="47e35-260">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="47e35-260">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="47e35-261">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="47e35-261">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="47e35-262">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="47e35-262">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="47e35-263">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="47e35-263">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="47e35-264">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="47e35-264">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="47e35-265">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="47e35-265">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="47e35-266">**Sistem** ad alanındaki bazı diğer değer türleri farklı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="47e35-266">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="47e35-267">Yönetilmeyen kodun bu türler için zaten iyi belirlenmiş biçimleri olduğundan, Sıralayıcı bunları hazırlamayı sağlayacak özel kurallara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="47e35-267">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="47e35-268">Aşağıdaki tabloda, **sistem** ad alanındaki özel değer türlerinin yanı sıra, sıralandıkları yönetilmeyen tür listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="47e35-268">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="47e35-269">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="47e35-269">System value type</span></span>|<span data-ttu-id="47e35-270">IDL türü</span><span class="sxs-lookup"><span data-stu-id="47e35-270">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="47e35-271">**GÜNCEL**</span><span class="sxs-lookup"><span data-stu-id="47e35-271">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="47e35-272">**KATEGORI**</span><span class="sxs-lookup"><span data-stu-id="47e35-272">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="47e35-273">**'INI**</span><span class="sxs-lookup"><span data-stu-id="47e35-273">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="47e35-274">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="47e35-274">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="47e35-275">Aşağıdaki kodda, Stdole2 tür kitaplığındaki yönetilmeyen türlerin **tarihi**, **GUID**, **DECIMAL**ve **OLE_COLOR** tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47e35-275">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="47e35-276">Tür kitaplığı temsili</span><span class="sxs-lookup"><span data-stu-id="47e35-276">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="47e35-277">Aşağıdaki kod, yönetilen arabirimde karşılık gelen tanımları gösterir `IValueTypes` .</span><span class="sxs-lookup"><span data-stu-id="47e35-277">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="47e35-278">Tür kitaplığı temsili</span><span class="sxs-lookup"><span data-stu-id="47e35-278">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="47e35-279">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47e35-279">See also</span></span>

- [<span data-ttu-id="47e35-280">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="47e35-280">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="47e35-281">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="47e35-281">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="47e35-282">Diziler için Varsayılan Sıralama</span><span class="sxs-lookup"><span data-stu-id="47e35-282">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="47e35-283">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="47e35-283">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="47e35-284">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="47e35-284">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
