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
ms.openlocfilehash: 6bf6acc719b4697534e845f64890ddcd9cac550f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315770"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="804c5-102">Varsayılan Sıralama Davranışı</span><span class="sxs-lookup"><span data-stu-id="804c5-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="804c5-103">Birlikte çalışma hazırlama kurallar arasında yönetilen ve yönetilmeyen bellek geçerken yöntem parametreleri ile ilişkili verileri nasıl davranacağını bu dikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="804c5-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="804c5-104">Yerleşik kurallar bir çağrılan geçirilen verileri değiştirebilir ve bu değişiklikleri çağırana döndürmesi ve performans iyileştirmelerini sağlayıp altında Sıralayıcı koşulda veri türü dönüşümleri olarak sıralama gibi etkinlikler denetler.</span><span class="sxs-lookup"><span data-stu-id="804c5-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="804c5-105">Bu bölümde, birlikte çalışma hazırlama hizmet varsayılan davranış özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="804c5-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="804c5-106">Bu, diziler, Boole türleri, char türü, temsilciler, sınıflar, nesneleri, dizeleri ve yapıları hazırlama hakkında ayrıntılı bilgi sunar.</span><span class="sxs-lookup"><span data-stu-id="804c5-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804c5-107">Genel türlerin sıralama desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="804c5-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="804c5-108">Daha fazla bilgi edinmek, [birlikte çalışma genel türleri kullanarak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="804c5-108">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="804c5-109">Birlikte çalışma sıralayıcısı ile bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="804c5-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="804c5-110">Birlikte çalışma sıralayıcısı, yönetilmeyen kod tarafından ayrılan bellek boşaltmak her zaman çalışır.</span><span class="sxs-lookup"><span data-stu-id="804c5-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="804c5-111">Bu davranışı COM bellek yönetimi kuralları ile uyumludur, ancak yerel C++ yöneten kuralları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="804c5-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="804c5-112">(Hiçbir bellek serbest bırakma) yerel C++ davranışını düşünüyorsanız karışıklık çıkabilir zaman platformunu kullanarak çağırmak, hangi otomatik olarak işaretçiler için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="804c5-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="804c5-113">Örneğin, aşağıdaki yönetilmeyen C++ DLL'den metodunu otomatik olarak herhangi bir bellek boş değil.</span><span class="sxs-lookup"><span data-stu-id="804c5-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="804c5-114">Yönetilmeyen imzası</span><span class="sxs-lookup"><span data-stu-id="804c5-114">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="804c5-115">Ancak, her bir platform çağırma gibi prototip yöntemi tanımlarsanız, değiştirin **BSTR** tür bir <xref:System.String> yazın ve arama `MethodOne`, ortak dil çalışma zamanı ücretsiz dener `b` iki kez.</span><span class="sxs-lookup"><span data-stu-id="804c5-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="804c5-116">Kullanarak da hazırlama davranışını değiştirebilirsiniz <xref:System.IntPtr> türleri yerine **dize** türleri.</span><span class="sxs-lookup"><span data-stu-id="804c5-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="804c5-117">Çalışma zamanı, her zaman kullanır **CoTaskMemFree** belleği boşaltmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="804c5-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="804c5-118">Birlikte çalıştığınız bellek ile ayrılıp değil **CoTaskMemAlloc** yöntemini kullanmalıdır bir **IntPtr** ve uygun yöntemi kullanarak el ile bellek.</span><span class="sxs-lookup"><span data-stu-id="804c5-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="804c5-119">Benzer şekilde, otomatik bellek boşaltma burada bellek hiçbir zaman bellekten kaldırılmalıdır durumlarda, tür kaçınabilirsiniz olarak kullanırken **GetCommandLine** işlevi Kernel32.dll dosyasından çekirdek bellek için bir işaretçi döndürür.</span><span class="sxs-lookup"><span data-stu-id="804c5-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="804c5-120">El ile bellek serbest bırakma hakkında daha fazla bilgi için bkz [arabellekler örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="804c5-120">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="804c5-121">Sınıflar için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="804c5-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="804c5-122">Sınıflar yalnızca COM birlikte çalışma tarafından sıralanabilir ve her zaman arabirimleri olarak sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="804c5-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="804c5-123">Bazı durumlarda, sınıf hazırlamak için kullanılan arabirimi sınıf arabirimi bilinir.</span><span class="sxs-lookup"><span data-stu-id="804c5-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="804c5-124">Tercih ettiğiniz bir arabirime sahip sınıf arabirimi geçersiz kılma hakkında daha fazla bilgi için bkz: [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="804c5-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="804c5-125">COM sınıflarına geçirme</span><span class="sxs-lookup"><span data-stu-id="804c5-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="804c5-126">Yönetilen bir sınıf için COM geçirildiğinde, birlikte çalışma sıralayıcısı, otomatik olarak bir COM Ara sunucu ile sınıfa sarmalar ve COM yöntem çağrısına Ara sunucu tarafından üretilen sınıf arabirimi geçirir.</span><span class="sxs-lookup"><span data-stu-id="804c5-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="804c5-127">Proxy, ardından tüm çağrılarda sınıf arabirimi yönetilen nesnesine atar.</span><span class="sxs-lookup"><span data-stu-id="804c5-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="804c5-128">Proxy sınıfı tarafından açıkça uygulanmaz ve diğer arabirimleri de sunar.</span><span class="sxs-lookup"><span data-stu-id="804c5-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="804c5-129">Proxy otomatik olarak arabirimlerini gibi uygular **IUnknown** ve **IDispatch** adına sınıfı.</span><span class="sxs-lookup"><span data-stu-id="804c5-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="804c5-130">.NET kodu sınıflarına geçirme</span><span class="sxs-lookup"><span data-stu-id="804c5-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="804c5-131">COM yöntemi bağımsız değişken olarak coclass'ları genellikle kullanılmaz</span><span class="sxs-lookup"><span data-stu-id="804c5-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="804c5-132">Bunun yerine, varsayılan bir arabirim yerine coclass'ı genellikle geçirilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="804c5-133">Bir arabirim yönetilen koda geçirildiğinde, doğru sarmalayıcı arabirimiyle sarmalama ve sarmalayıcı yönetilen yönteme geçirmek için birlikte çalışma sıralayıcısı sorumludur.</span><span class="sxs-lookup"><span data-stu-id="804c5-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="804c5-134">Belirleme kullanmak için hangi sarmalayıcı zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="804c5-135">Her bir COM nesnesinin örneği benzersiz, tek bir sarmalayıcı kaç arabirimleri ne olursa olsun nesne uygulayan sahiptir.</span><span class="sxs-lookup"><span data-stu-id="804c5-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="804c5-136">Örneğin, yalnızca bir sarmalayıcı beş farklı arabirimleri uygulayan tek bir COM nesnesi vardır.</span><span class="sxs-lookup"><span data-stu-id="804c5-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="804c5-137">Aynı kapsayıcı tüm beş arabirimleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="804c5-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="804c5-138">İki örneğini COM nesnesi oluşturulur, ardından sarmalayıcı iki örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="804c5-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="804c5-139">Sarmalayıcı ömrü boyunca aynı türde korumak, nesne tarafından sunulan bir arabirim Sıralayıcı geçirilen ilk kez doğru sarmalayıcı birlikte çalışma sıralayıcısı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="804c5-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="804c5-140">Sıralayıcı nesne uygulayan arabirimlerinden birini bakarak nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="804c5-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="804c5-141">Örneğin, Sıralayıcı sınıfı sarmalayıcı yönetilen koda geçirildi arabirimi sarmalamak için kullanılması gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="804c5-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="804c5-142">Arabirimi Sıralayıcı ilk geçirildiğinde, Sıralayıcı arabirimi bilinen bir nesneden kullanıma sunulacak olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="804c5-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="804c5-143">Bu denetim, iki durumda gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="804c5-143">This check occurs in two situations:</span></span>  
  
-   <span data-ttu-id="804c5-144">Bir arabirim için COM başka bir yerde geçirildi başka bir yönetilen nesne tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="804c5-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="804c5-145">Sıralayıcı yönetilen nesneler tarafından kullanıma sunulan arabirimler kolayca tanımlayabilirsiniz ve arabirim uygulamasını sağlayan yönetilen bir nesne ile eşleşecek şekilde edebilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="804c5-146">Yönetilen Nesne sonra yöntemine geçirilir ve hiçbir sarmalayıcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="804c5-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
-   <span data-ttu-id="804c5-147">Zaten sarmalanmış bir nesne arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="804c5-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="804c5-148">Durumun bu olup olmadığını belirlemek için nesne için sıralayıcı sorgular, **IUnknown** arabirim ve döndürülen arabirim sarmalanır ve diğer nesnelerin arabirimlere karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="804c5-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="804c5-149">Arabirimi, başka bir sarmalayıcı aynı olduğunda, nesneler aynı kimliğe sahip ve mevcut sarmalayıcı yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="804c5-150">Sıralayıcı, bilinen bir nesneden bir arabirim değil, şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="804c5-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="804c5-151">Nesne için sıralayıcı sorgular **IProvideClassInfo2** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="804c5-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="804c5-152">Sağlanırsa, döndürülen CLSID Sıralayıcı kullanan **IProvideClassInfo2.GetGUID** arayüzü sağlama coclass'ı tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="804c5-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="804c5-153">Derleme önceden kayıtlı olup olmadığını CLSID ile kapsayıcı kayıt defterinden Sıralayıcı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="804c5-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="804c5-154">Arabirim için sıralayıcı sorgular **Iprovideclassınfo** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="804c5-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="804c5-155">Sağladıysanız Sıralayıcı kullanan **ITypeInfo** döndürüldüğü **IProvideClassInfo.GetClassinfo** arabirimi gösterme sınıfı CLSID değeri belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="804c5-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="804c5-156">Sıralayıcı CLSID sarmalayıcı için meta verileri bulmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="804c5-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="804c5-157">Sıralayıcı hala sınıfı tanımlanamıyor, adlı bir genel sarmalayıcı sınıf arabirimi sarmalar **System.comobject'e**.</span><span class="sxs-lookup"><span data-stu-id="804c5-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="804c5-158">Temsilciler için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="804c5-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="804c5-159">Yönetilen bir temsilci, bir COM arabirimi veya çağıran mekanizmasına dayalı bir işlev işaretçisi olarak sıralanır:</span><span class="sxs-lookup"><span data-stu-id="804c5-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
-   <span data-ttu-id="804c5-160">İçin platform çağırma, varsayılan olarak bir temsilci bir yönetilmeyen işlev işaretçisi sıralanır.</span><span class="sxs-lookup"><span data-stu-id="804c5-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
-   <span data-ttu-id="804c5-161">COM birlikte çalışması için bir temsilci türü bir COM arabirimi sıralanır **_Delegate** varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="804c5-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="804c5-162">**_Delegate** arabirimi Mscorlib.tlb tür kitaplığında tanımlanan ve içeren <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> başvuran temsilci yöntemi çağırma olanak tanıyan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="804c5-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="804c5-163">Aşağıdaki tabloda, yönetilen temsilci veri türü için sıralama seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="804c5-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="804c5-164"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği sağlayan çeşitli <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesi değerleri sıralama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="804c5-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="804c5-165">Numaralandırma türü</span><span class="sxs-lookup"><span data-stu-id="804c5-165">Enumeration type</span></span>|<span data-ttu-id="804c5-166">Yönetilmeyen biçimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="804c5-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|**<span data-ttu-id="804c5-167">UnmanagedType.FunctionPtr</span><span class="sxs-lookup"><span data-stu-id="804c5-167">UnmanagedType.FunctionPtr</span></span>**|<span data-ttu-id="804c5-168">Bir yönetilmeyen işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="804c5-168">An unmanaged function pointer.</span></span>|  
|**<span data-ttu-id="804c5-169">UnmanagedType.Interface</span><span class="sxs-lookup"><span data-stu-id="804c5-169">UnmanagedType.Interface</span></span>**|<span data-ttu-id="804c5-170">Bir arabirim türü **_Delegate**Mscorlib.tlb içinde tanımlanan gibi.</span><span class="sxs-lookup"><span data-stu-id="804c5-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="804c5-171">Aşağıdaki kod örneği göz önünde bulundurun yöntemlerinin `DelegateTestInterface` bir COM tür kitaplığı dışarı aktarılır.</span><span class="sxs-lookup"><span data-stu-id="804c5-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="804c5-172">Yalnızca temsilci bildirimi ile işaretlenen **ref** (veya **ByRef**) anahtar sözcüğü In/Out parametresi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="804c5-173">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="804c5-173">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="804c5-174">Yalnızca diğer herhangi bir yönetilmeyen bir işleve işaretçi başvurusu olarak, bir işlev işaretçisi başvurusunun.</span><span class="sxs-lookup"><span data-stu-id="804c5-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="804c5-175">Bu örnekte, iki temsilci olarak sıralandığı zaman <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, sonuç bir `int` ve işaretçi bir `int`.</span><span class="sxs-lookup"><span data-stu-id="804c5-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="804c5-176">Temsilci türleri başvuruya çünkü `int` burada için bir void bir işaretçi temsil eder (`void*`), bellekte temsilci adresini olduğu.</span><span class="sxs-lookup"><span data-stu-id="804c5-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="804c5-177">Diğer bir deyişle, bu tarihten sonra 32 bit Windows sistemlerine sonucudur `int` burada işlev işaretçisi boyutunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="804c5-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
>  <span data-ttu-id="804c5-178">İşlev işaretçisi tarafından yönetilmeyen kod tutulan, yönetilen bir temsilci bir başvuru ortak dil çalışma zamanı, çöp toplama yönetilen bir nesnede gerçekleştirmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="804c5-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="804c5-179">Örneğin, aşağıdaki kodu yanlış olduğundan başvuru `cb` nesnesi, geçirilen `SetChangeHandler` yöntemi saklamaz `cb` ömrünü dışında tutma `Test` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="804c5-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="804c5-180">Bir kez `cb` çöp olarak toplanacak nesnedir, işlev işaretçisi geçirilen `SetChangeHandler` artık geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="804c5-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="804c5-181">Beklenmeyen bir çöp toplama için dengelemek için çağıranın emin olmanız gerekir `cb` yönetilmeyen işlev işaretçisi kullanımda olduğu sürece nesne Canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="804c5-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="804c5-182">İsteğe bağlı olarak, yönetilen kod işlev işaretçisi artık, aşağıdaki örnekte gösterildiği gibi gerekli olduğunda bildirim yönetilmeyen kod olabilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="804c5-183">Değer türleri için varsayılan sıralama</span><span class="sxs-lookup"><span data-stu-id="804c5-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="804c5-184">Tamsayı ve kayan nokta numaraları gibi birçok değer türleri [blittable](blittable-and-non-blittable-types.md) ve hazırlama gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="804c5-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="804c5-185">Diğer [kopyalanamaz](blittable-and-non-blittable-types.md) türleri yönetilen ve yönetilmeyen bellekte farklı temsilleri olabilir ve hazırlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="804c5-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="804c5-186">Yine de diğer türler, açık birlikte çalışabilirlik sınırında biçimlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="804c5-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="804c5-187">Bu bölüm, aşağıdaki biçimlendirilen değer türlerinde bilgileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="804c5-187">This section provides information on the following formatted value types:</span></span>  
  
-   [<span data-ttu-id="804c5-188">Değer türleri platformunda kullanılan çağırma</span><span class="sxs-lookup"><span data-stu-id="804c5-188">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
-   [<span data-ttu-id="804c5-189">COM birlikte çalışma kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="804c5-189">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="804c5-190">Biçimlendirilmiş türlerini açıklayan ek olarak, bu konu tanımlar [sistem değer türleri](#system-value-types) olağan dışı hazırlama davranışı vardır.</span><span class="sxs-lookup"><span data-stu-id="804c5-190">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="804c5-191">Biçimlendirilmiş bir tür üyelerini bellekte düzenini açıkça denetleyen bilgilerini içeren karmaşık bir türdür.</span><span class="sxs-lookup"><span data-stu-id="804c5-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="804c5-192">Üye düzeni bilgilerini kullanarak sağlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="804c5-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="804c5-193">Düzeni aşağıdakilerden biri olabilir <xref:System.Runtime.InteropServices.LayoutKind> sabit listesi değerleri:</span><span class="sxs-lookup"><span data-stu-id="804c5-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
-   **<span data-ttu-id="804c5-194">LayoutKind.Automatic</span><span class="sxs-lookup"><span data-stu-id="804c5-194">LayoutKind.Automatic</span></span>**  
  
     <span data-ttu-id="804c5-195">Ortak dil çalışma zamanı verimliliği için türün üyeleri yeniden sıralamak ücretsiz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="804c5-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="804c5-196">Ancak, yönetilmeyen koda bir değer türü geçirildiğinde, üyeleri düzenini öngörülebilir olur.</span><span class="sxs-lookup"><span data-stu-id="804c5-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="804c5-197">Böyle bir yapı otomatik olarak hazırlamak girişimi, bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="804c5-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
-   **<span data-ttu-id="804c5-198">LayoutKind.Sequential</span><span class="sxs-lookup"><span data-stu-id="804c5-198">LayoutKind.Sequential</span></span>**  
  
     <span data-ttu-id="804c5-199">Yönetilen tür tanımında göründükleri sırayla yönetilmeyen bellekte düzenlendiği için türün üyeleri olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="804c5-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
-   **<span data-ttu-id="804c5-200">LayoutKind.Explicit</span><span class="sxs-lookup"><span data-stu-id="804c5-200">LayoutKind.Explicit</span></span>**  
  
     <span data-ttu-id="804c5-201">Üyeleri göre düzenlenmiştir gösterir <xref:System.Runtime.InteropServices.FieldOffsetAttribute> her alanı ile sağlanan.</span><span class="sxs-lookup"><span data-stu-id="804c5-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="804c5-202">Değer türleri platformunda kullanılan çağırma</span><span class="sxs-lookup"><span data-stu-id="804c5-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="804c5-203">Aşağıdaki örnekte `Point` ve `Rect` türler, üye düzen bilgilerini sağlamak kullanarak **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="804c5-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="804c5-204">Bu biçimlendirilmiş türleri için yönetilmeyen kod sıralandığı zaman C stili yapıları olarak sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="804c5-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="804c5-205">Bu yapı bağımsız değişkenlere sahip bir yönetilmeyen API çağırmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="804c5-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="804c5-206">Örneğin, `POINT` ve `RECT` yapıları için Microsoft Windows API geçirilebilir **PtInRect** gibi işlev:</span><span class="sxs-lookup"><span data-stu-id="804c5-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="804c5-207">Yapıları geçirebilirsiniz platformu kullanarak çağırma tanımı:</span><span class="sxs-lookup"><span data-stu-id="804c5-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class WindowsAPI
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="804c5-208">`Rect` Değer türü yönetilmeyen API için bir işaretçi bekliyor olduğundan başvuru ile geçirilmelidir bir `RECT` işleve geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="804c5-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="804c5-209">`Point` Yönetilmeyen API beklediği değer türü değere göre geçirilir `POINT` yığında geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="804c5-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="804c5-210">Bu fark çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="804c5-210">This subtle difference is very important.</span></span> <span data-ttu-id="804c5-211">Başvuruları yönetilmeyen koda işaretçileri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="804c5-212">Değerleri, yönetilmeyen koda yığına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804c5-213">Biçimlendirilmiş bir tür bir yapı sıralanır, alanlar yalnızca türü içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="804c5-214">Tür yöntemleri, özellikleri veya olayları sahipse, yönetilmeyen koddan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="804c5-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="804c5-215">Sabit üye Düzen sağlanan sınıfları ayrıca yönetilmeyen koda C stili yapıları olarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="804c5-216">Bir sınıf üyesine ilişkin düzen bilgilerini de ile sağlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="804c5-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="804c5-217">Değer türleri ile arasındaki temel fark, bu da düzenin sabit ve sabit biçimli sınıflar, yönetilmeyen koda sıralanmış yoludur.</span><span class="sxs-lookup"><span data-stu-id="804c5-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="804c5-218">Değer türleri (yığın üzerinde) değere göre geçirilir ve sonuç olarak türün üyeleri için Aranan tarafından yapılan değişiklikler arayan tarafından görülmez.</span><span class="sxs-lookup"><span data-stu-id="804c5-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="804c5-219">Başvuru türleri (bir başvuru türü yığın üzerine geçirilir) başvuruyla geçirilir; Sonuç olarak, bir tür blittable-tür üyelerine Aranan tarafından yapılan tüm değişiklikler arayan tarafından görülür.</span><span class="sxs-lookup"><span data-stu-id="804c5-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804c5-220">Bir başvuru türü kopyalanamaz türlerin üyelerini varsa, dönüştürme iki kez gereklidir: ne zaman bir bağımsız değişken geçirilir yönetilmeyen yan ve ikinci ilk kez zaman çağrısından dönüşte.</span><span class="sxs-lookup"><span data-stu-id="804c5-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="804c5-221">Aranan tarafından yapılan değişiklikleri görmek çağıranın istiyorsa, bu nedenle eklenen yükü, In/Out parametreleri açıkça bir bağımsız değişken uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="804c5-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="804c5-222">Aşağıdaki örnekte, `SystemTime` sınıf üyesi sıralı düzene sahip ve Windows API'ye geçirilen **GetSystemTime** işlevi.</span><span class="sxs-lookup"><span data-stu-id="804c5-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="804c5-223">**GetSystemTime** işlevi şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="804c5-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="804c5-224">Eşdeğer platform çağırma tanımı **GetSystemTime** aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="804c5-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class WindowsAPI
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="804c5-225">Dikkat `SystemTime` çünkü bağımsız değişkeni bir başvuru bağımsız değişkeni değil yazılan `SystemTime` sınıfı, bir değer türü değil.</span><span class="sxs-lookup"><span data-stu-id="804c5-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="804c5-226">Değer türlerinin aksine, sınıflar her zaman başvuruyla geçirildi.</span><span class="sxs-lookup"><span data-stu-id="804c5-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="804c5-227">Aşağıdaki kod örneği farklı bir gösterir `Point` adlı yöntemi içeren sınıf `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="804c5-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="804c5-228">Ardışık Düzen türüne sahip olduğundan, yönetilmeyen kod için geçirilen ve bir yapı sıralanır.</span><span class="sxs-lookup"><span data-stu-id="804c5-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="804c5-229">Ancak, `SetXY` üye yönetilmeyen koddan çağrılabilir değil nesne başvuru tarafından geçirilmediğine olsa bile.</span><span class="sxs-lookup"><span data-stu-id="804c5-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="804c5-230">COM birlikte çalışma kullanılan değer türleri</span><span class="sxs-lookup"><span data-stu-id="804c5-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="804c5-231">Biçimlendirilmiş türleri COM birlikte çalışma yöntem çağrıları için de geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="804c5-232">Aslında, bir tür kitaplığına dışarı aktardığınızda, değer türleri otomatik olarak yapılarını dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="804c5-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="804c5-233">Aşağıdaki örnekte gösterildiği gibi `Point` değer türü olur (typedef) adlı bir tür tanımı `Point`.</span><span class="sxs-lookup"><span data-stu-id="804c5-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="804c5-234">Tüm başvuruları `Point` tür kitaplığı içindeki başka bir yerde değer türü ile değiştirilir `Point` typedef.</span><span class="sxs-lookup"><span data-stu-id="804c5-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 **<span data-ttu-id="804c5-235">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="804c5-235">Type library representation</span></span>**  
  
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
  
 <span data-ttu-id="804c5-236">Değerleri ve platform başvuruları hazırlamak için kullanılan aynı kurallara çağrılarını çağırmak COM arabirimleri sıralama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="804c5-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="804c5-237">Örneğin, örneği `Point` değer türü, COM, .NET Framework'den geçirilir `Point` değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="804c5-238">Varsa `Point` değer türü bir işaretçi, başvuru tarafından geçirilen bir `Point` yığına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="804c5-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="804c5-239">Birlikte çalışma sıralayıcısı, yüksek düzeyde yöneltme desteklemez (**noktası** \* \*) herhangi bir yönde.</span><span class="sxs-lookup"><span data-stu-id="804c5-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804c5-240">Yapıları sahip <xref:System.Runtime.InteropServices.LayoutKind> sabit listesi değeri **açık** dışarı aktarılan tür kitaplığı açık bir düzen express olamaz COM birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="804c5-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="804c5-241">Sistem değer türleri</span><span class="sxs-lookup"><span data-stu-id="804c5-241">System Value Types</span></span>  
 <span data-ttu-id="804c5-242"><xref:System> Ad alanı olan çalışma zamanı temel türleri paketlenmiş biçiminde temsil eden birden çok değer türleri.</span><span class="sxs-lookup"><span data-stu-id="804c5-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="804c5-243">Örneğin, değer türü <xref:System.Int32?displayProperty=nameWithType> yapısı temsil eder, kutulanmış biçiminde **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="804c5-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="804c5-244">Biçimlendirilmiş diğer türler gibi bu tür yapıları olarak hazırlama yerine, bunları bunlar kutusunda ilkel türler olarak aynı şekilde hazırlama.</span><span class="sxs-lookup"><span data-stu-id="804c5-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="804c5-245">**System.Int32** olarak bu nedenle sıralanmış **ELEMENT_TYPE_I4** yerine tek bir üye türü içeren bir yapıya olarak **uzun**.</span><span class="sxs-lookup"><span data-stu-id="804c5-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="804c5-246">Aşağıdaki tabloda değer türlerinin bir listesini içeren **sistem** paketlenmiş temsillerini ilkel türleri olan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="804c5-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="804c5-247">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="804c5-247">System value type</span></span>|<span data-ttu-id="804c5-248">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="804c5-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|**<span data-ttu-id="804c5-249">ELEMENT_TYPE_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="804c5-249">ELEMENT_TYPE_BOOLEAN</span></span>**|  
|<xref:System.SByte?displayProperty=nameWithType>|**<span data-ttu-id="804c5-250">ELEMENT_TYPE_I1</span><span class="sxs-lookup"><span data-stu-id="804c5-250">ELEMENT_TYPE_I1</span></span>**|  
|<xref:System.Byte?displayProperty=nameWithType>|**<span data-ttu-id="804c5-251">ELEMENT_TYPE_UI1</span><span class="sxs-lookup"><span data-stu-id="804c5-251">ELEMENT_TYPE_UI1</span></span>**|  
|<xref:System.Char?displayProperty=nameWithType>|**<span data-ttu-id="804c5-252">ELEMENT_TYPE_CHAR</span><span class="sxs-lookup"><span data-stu-id="804c5-252">ELEMENT_TYPE_CHAR</span></span>**|  
|<xref:System.Int16?displayProperty=nameWithType>|**<span data-ttu-id="804c5-253">ELEMENT_TYPE_I2</span><span class="sxs-lookup"><span data-stu-id="804c5-253">ELEMENT_TYPE_I2</span></span>**|  
|<xref:System.UInt16?displayProperty=nameWithType>|**<span data-ttu-id="804c5-254">ELEMENT_TYPE_U2</span><span class="sxs-lookup"><span data-stu-id="804c5-254">ELEMENT_TYPE_U2</span></span>**|  
|<xref:System.Int32?displayProperty=nameWithType>|**<span data-ttu-id="804c5-255">ELEMENT_TYPE_I4</span><span class="sxs-lookup"><span data-stu-id="804c5-255">ELEMENT_TYPE_I4</span></span>**|  
|<xref:System.UInt32?displayProperty=nameWithType>|**<span data-ttu-id="804c5-256">ELEMENT_TYPE_U4</span><span class="sxs-lookup"><span data-stu-id="804c5-256">ELEMENT_TYPE_U4</span></span>**|  
|<xref:System.Int64?displayProperty=nameWithType>|**<span data-ttu-id="804c5-257">ELEMENT_TYPE_I8</span><span class="sxs-lookup"><span data-stu-id="804c5-257">ELEMENT_TYPE_I8</span></span>**|  
|<xref:System.UInt64?displayProperty=nameWithType>|**<span data-ttu-id="804c5-258">ELEMENT_TYPE_U8</span><span class="sxs-lookup"><span data-stu-id="804c5-258">ELEMENT_TYPE_U8</span></span>**|  
|<xref:System.Single?displayProperty=nameWithType>|**<span data-ttu-id="804c5-259">ELEMENT_TYPE_R4</span><span class="sxs-lookup"><span data-stu-id="804c5-259">ELEMENT_TYPE_R4</span></span>**|  
|<xref:System.Double?displayProperty=nameWithType>|**<span data-ttu-id="804c5-260">ELEMENT_TYPE_R8</span><span class="sxs-lookup"><span data-stu-id="804c5-260">ELEMENT_TYPE_R8</span></span>**|  
|<xref:System.String?displayProperty=nameWithType>|**<span data-ttu-id="804c5-261">ELEMENT_TYPE_STRING</span><span class="sxs-lookup"><span data-stu-id="804c5-261">ELEMENT_TYPE_STRING</span></span>**|  
|<xref:System.IntPtr?displayProperty=nameWithType>|**<span data-ttu-id="804c5-262">ELEMENT_TYPE_I</span><span class="sxs-lookup"><span data-stu-id="804c5-262">ELEMENT_TYPE_I</span></span>**|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|**<span data-ttu-id="804c5-263">ELEMENT_TYPE_U</span><span class="sxs-lookup"><span data-stu-id="804c5-263">ELEMENT_TYPE_U</span></span>**|  
  
 <span data-ttu-id="804c5-264">Başka bir değer türleri içinde **sistem** ad alanı farklı bir şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="804c5-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="804c5-265">Sıralayıcı, yönetilmeyen kod için bu tür tanınmış biçimler olduğundan, bunları hazırlama için özel kurallar vardır.</span><span class="sxs-lookup"><span data-stu-id="804c5-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="804c5-266">Özel değer türleri aşağıdaki tabloda **sistem** ad alanı, bunlar için hazırlanır yönetilmeyen tür yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="804c5-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="804c5-267">Sistem değer türü</span><span class="sxs-lookup"><span data-stu-id="804c5-267">System value type</span></span>|<span data-ttu-id="804c5-268">IDL türü</span><span class="sxs-lookup"><span data-stu-id="804c5-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**<span data-ttu-id="804c5-269">DATE</span><span class="sxs-lookup"><span data-stu-id="804c5-269">DATE</span></span>**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**<span data-ttu-id="804c5-270">DECIMAL</span><span class="sxs-lookup"><span data-stu-id="804c5-270">DECIMAL</span></span>**|  
|<xref:System.Guid?displayProperty=nameWithType>|**<span data-ttu-id="804c5-271">GUID</span><span class="sxs-lookup"><span data-stu-id="804c5-271">GUID</span></span>**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**<span data-ttu-id="804c5-272">OLE_COLOR</span><span class="sxs-lookup"><span data-stu-id="804c5-272">OLE_COLOR</span></span>**|  
  
 <span data-ttu-id="804c5-273">Aşağıdaki kod, yönetilmeyen türlerinin tanımını göstermektedir **tarih**, **GUID**, **ondalık**, ve **OLE_COLOR** Stdole2 türü Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="804c5-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="804c5-274">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="804c5-274">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="804c5-275">Aşağıdaki kod, karşılık gelen tanımları yönetilen gösterir `IValueTypes` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="804c5-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="804c5-276">Tür kitaplığı gösterimi</span><span class="sxs-lookup"><span data-stu-id="804c5-276">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="804c5-277">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="804c5-277">See also</span></span>

- [<span data-ttu-id="804c5-278">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="804c5-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="804c5-279">Kopyalama ve Sabitleme</span><span class="sxs-lookup"><span data-stu-id="804c5-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="804c5-280">Diziler için Varsayılan Sıralama</span><span class="sxs-lookup"><span data-stu-id="804c5-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="804c5-281">Nesneler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="804c5-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="804c5-282">Dizeler için Varsayılan Hazırlama</span><span class="sxs-lookup"><span data-stu-id="804c5-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
