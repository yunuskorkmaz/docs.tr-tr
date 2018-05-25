---
title: COM Aranabilir Sarmalayıcısı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21f7b0d56a788b4161fb7e99899b4dd15a434152
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="dbfa0-102">COM Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="dbfa0-102">COM Callable Wrapper</span></span>
<span data-ttu-id="dbfa0-103">COM istemcisi .NET nesnesi aradığında, ortak dil çalışma zamanı yönetilen nesneyi ve nesne için bir COM aranabilir sarmalayıcısı (saat) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="dbfa0-104">Bir .NET nesnesine başvuru için doğrudan COM istemcileri saatin tersi YÖNDE bir proxy olarak yönetilen nesne için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>  
  
 <span data-ttu-id="dbfa0-105">Çalışma zamanı hizmetlerinin isteyen COM istemcileri sayısından bağımsız olarak yönetilen bir nesne için tam olarak bir saat oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="dbfa0-106">Aşağıdaki çizimde gösterildiği gibi birden çok COM istemcileri INew arabirimi kullanıma sunan saatin tersi YÖNDE başvuru basılı tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="dbfa0-107">Saatin tersi YÖNDE, sırasıyla arabirimini uygulayan yönetilen nesne için tek bir başvuru tutar ve atık toplanır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="dbfa0-108">COM ve .NET istemcileri, istekleri için aynı anda aynı yönetilen nesne üzerinde hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>  
  
 <span data-ttu-id="dbfa0-109">![COM aranabilir sarmalayıcısı](./media/ccw.gif "saatin tersi yönde")</span><span class="sxs-lookup"><span data-stu-id="dbfa0-109">![COM callable wrapper](./media/ccw.gif "ccw")</span></span>  
<span data-ttu-id="dbfa0-110">COM aranabilir sarmalayıcısı .NET nesnelere erişme</span><span class="sxs-lookup"><span data-stu-id="dbfa0-110">Accessing .NET objects through COM callable wrapper</span></span>  
  
 <span data-ttu-id="dbfa0-111">COM aranabilir sarmalayıcılar, .NET Framework içinde çalışan diğer sınıflara görünmez.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-111">COM callable wrappers are invisible to other classes running within the .NET Framework.</span></span> <span data-ttu-id="dbfa0-112">Yönetilen ve yönetilmeyen kodu arasında çağrılarını sıralamakta kendi birincil amacı olan; Ancak, CCWs nesne kimliği ve bunlar sarmalamak yönetilen nesnelerin nesne ömrü yönetin.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-112">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>  
  
## <a name="object-identity"></a><span data-ttu-id="dbfa0-113">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="dbfa0-113">Object Identity</span></span>  
 <span data-ttu-id="dbfa0-114">Çalışma zamanı gerektiği gibi bellekteki nesne hareket etmek çalışma zamanı sağlayan kendi çöpünün toplanma yığın, gelen .NET nesnesi için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-114">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="dbfa0-115">Buna karşılık, çalışma zamanı sarmalayıcı doğrudan başvurmak COM istemcileri için olası hale getirerek noncollected bir öbek gelen için saatin tersi YÖNDE bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-115">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>  
  
## <a name="object-lifetime"></a><span data-ttu-id="dbfa0-116">Nesne ömrü</span><span class="sxs-lookup"><span data-stu-id="dbfa0-116">Object Lifetime</span></span>  
 <span data-ttu-id="dbfa0-117">Sarmaladığı .NET istemcilerin aksine, saatin tersi YÖNDE başvuru-geleneksel COM şekilde sayılır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-117">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="dbfa0-118">Saatin tersi YÖNDE başvuru sayısı sıfır ulaştığında sarmalayıcı yönetilen nesne üzerinde kendi başvuru serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-118">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="dbfa0-119">Kalan başvuru ile yönetilen bir nesnenin sonraki çöp toplama döngüsü sırasında toplanır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-119">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>  
  
## <a name="simulating-com-interfaces"></a><span data-ttu-id="dbfa0-120">COM arabirimleri benzetimini yapma</span><span class="sxs-lookup"><span data-stu-id="dbfa0-120">Simulating COM interfaces</span></span>

<span data-ttu-id="dbfa0-121">Saatin tersi YÖNDE tüm ortak, COM görünebilir arabirimler, veri türleri ve dönüş değerleri COM istemcilere arabirimi tabanlı etkileşim COM'ın zorlama ile tutarlı bir şekilde kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-121">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="dbfa0-122">COM istemcisi için bir .NET Framework nesne üzerinde yöntemleri çağrılırken bir COM nesnesinin yöntemlerde çağırmak için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-122">For a COM client, invoking methods on a .NET Framework object is identical to invoking methods on a COM object.</span></span>  
  
 <span data-ttu-id="dbfa0-123">Bu sorunsuz bir yaklaşım oluşturmak için saatin tersi YÖNDE geleneksel COM arabirimleri gibi üreten **IUnknown** ve **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-123">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="dbfa0-124">Aşağıdaki çizimde gösterildiği gibi saatin tersi YÖNDE sarmaladığı .NET nesnesi üzerinde tek bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-124">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="dbfa0-125">COM istemcisi ve .NET nesne birbiriyle CCW. proxy ve saplama yapımı etkileşim</span><span class="sxs-lookup"><span data-stu-id="dbfa0-125">Both the COM client and .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>  
  
 <span data-ttu-id="dbfa0-126">![COM arabirimleri](./media/ccwwithinterfaces.gif "ccwwithinterfaces")</span><span class="sxs-lookup"><span data-stu-id="dbfa0-126">![COM interfaces](./media/ccwwithinterfaces.gif "ccwwithinterfaces")</span></span>  
<span data-ttu-id="dbfa0-127">COM arabirimleri ve COM aranabilir sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="dbfa0-127">COM interfaces and the COM callable wrapper</span></span>  
  
 <span data-ttu-id="dbfa0-128">Yönetilen ortamda bir sınıf tarafından açıkça uygulanan arabirimler gösterme ek olarak, .NET Framework uygulamaları nesne adına aşağıdaki tabloda listelenen COM arabirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-128">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET Framework supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="dbfa0-129">Bir .NET sınıfı, kendi uygulama bu arabirimleri sağlayarak varsayılan davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-129">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="dbfa0-130">Ancak, çalışma zamanı uygulamasını her zaman sağlar **IUnknown** ve **IDispatch** arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-130">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>  
  
|<span data-ttu-id="dbfa0-131">Arabirim</span><span class="sxs-lookup"><span data-stu-id="dbfa0-131">Interface</span></span>|<span data-ttu-id="dbfa0-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbfa0-132">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbfa0-133">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-133">**Idispatch**</span></span>|<span data-ttu-id="dbfa0-134">Geç bağlama türü bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-134">Provides a mechanism for late binding to type.</span></span>|  
|<span data-ttu-id="dbfa0-135">**IerrorInfo**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-135">**IerrorInfo**</span></span>|<span data-ttu-id="dbfa0-136">Hata, kaynağı, bir Yardım dosyası, Yardım içeriği ve hata tanımlı arabirimi GUID metinsel açıklaması sağlar (her zaman **GUID_NULL** .NET sınıfları için).</span><span class="sxs-lookup"><span data-stu-id="dbfa0-136">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|  
|<span data-ttu-id="dbfa0-137">**IprovideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-137">**IprovideClassInfo**</span></span>|<span data-ttu-id="dbfa0-138">Erişim kazanmak COM istemcilerinde etkinleştirir **ITypeInfo** yönetilen bir sınıf tarafından uygulanan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-138">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span>|  
|<span data-ttu-id="dbfa0-139">**IsupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-139">**IsupportErrorInfo**</span></span>|<span data-ttu-id="dbfa0-140">Yönetilen Nesne destekleyip desteklemediğini belirlemek bir COM istemcisi sağlar **IErrorInfo** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-140">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="dbfa0-141">Bu durumda, son özel durum nesnesi için bir işaretçi almak istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-141">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="dbfa0-142">Tüm yönetilen türleri Destek **IErrorInfo** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-142">All managed types support the **IErrorInfo** interface.</span></span>|  
|<span data-ttu-id="dbfa0-143">**ITypeInfo**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-143">**ItypeInfo**</span></span>|<span data-ttu-id="dbfa0-144">Tlbexp.exe tarafından üretilen türü bilgileri tam olarak aynıdır bir sınıf için tür bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-144">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|  
|<span data-ttu-id="dbfa0-145">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-145">**Iunknown**</span></span>|<span data-ttu-id="dbfa0-146">Standart uygulamasını sağlar **IUnknown** hangi COM istemcisi saatin tersi YÖNDE ömrü yönetir ve türü zorlama sağlar arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-146">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|  
  
 <span data-ttu-id="dbfa0-147">Yönetilen bir sınıf, aşağıdaki tabloda açıklanan COM arabirimleri de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-147">A managed class can also provide the COM interfaces described in the following table.</span></span>  
  
|<span data-ttu-id="dbfa0-148">Arabirim</span><span class="sxs-lookup"><span data-stu-id="dbfa0-148">Interface</span></span>|<span data-ttu-id="dbfa0-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbfa0-149">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbfa0-150">(\_*Classname*) sınıf arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbfa0-150">The (\_*classname*) class interface</span></span>|<span data-ttu-id="dbfa0-151">Çalışma zamanı tarafından kullanıma sunulan ve açıkça tanımlanmış arabirimi, tüm ortak arabirimleri, yöntemler, özellikler ve yönetilen bir nesne üzerinde açıkça gösterilen alanları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-151">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|  
|<span data-ttu-id="dbfa0-152">**IConnectionPoint** ve **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-152">**IConnectionPoint** and **IconnectionPointContainer**</span></span>|<span data-ttu-id="dbfa0-153">Temsilci tabanlı olaylar (olay aboneleri kaydettirmek için bir arabirim) kaynak nesneler için arabirim.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-153">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|  
|<span data-ttu-id="dbfa0-154">**Idispatchex**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-154">**IdispatchEx**</span></span>|<span data-ttu-id="dbfa0-155">Sınıf uyguluyorsa çalışma zamanı tarafından sağlanan arabirim **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-155">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="dbfa0-156">**Idispatchex** arabirimi uzantısıdır **IDispatch** aksine, arabirim **IDispatch**, numaralandırma, ekleme, silme, sağlar ve büyük küçük harfe duyarlı üyeleri çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-156">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|  
|<span data-ttu-id="dbfa0-157">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="dbfa0-157">**IEnumVARIANT**</span></span>|<span data-ttu-id="dbfa0-158">Arabirim koleksiyon türü sınıfları için sınıf uyguluyorsa, koleksiyonundaki nesneleri numaralandırır **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-158">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|  
  
## <a name="introducing-the-class-interface"></a><span data-ttu-id="dbfa0-159">Sınıf arabirimi Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="dbfa0-159">Introducing the class interface</span></span>  
 <span data-ttu-id="dbfa0-160">Açıkça yönetilen kodda tanımlı değil, sınıf arabirimi tüm genel yöntemler, özellikler, alanları ve .NET nesne üzerinde açıkça gösterilen olayları gösteren bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-160">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="dbfa0-161">Bu arabirim, bir çift veya yalnızca gönderme arabirimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-161">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="dbfa0-162">Sınıf arabirimi bir çizgiyle öncesinde .NET sınıfın kendisi adını alır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-162">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="dbfa0-163">Örneğin, Mammal sınıfı için sınıf arabirimidir \_Mammal.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-163">For example, for class Mammal, the class interface is \_Mammal.</span></span>  
  
 <span data-ttu-id="dbfa0-164">Türetilen sınıflar için sınıf arabirimi tüm genel yöntemler, özellikler ve temel sınıfın alanları gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-164">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="dbfa0-165">Türetilmiş sınıf ayrıca her taban sınıfı için sınıf arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-165">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="dbfa0-166">Örneğin, sınıf Mammal MammalSuperclass sınıfını genişletir, kendisi System.Object genişletir, COM istemcileri için .NET nesne düzenlemenizi sağlayan üç adlı arabirimleri sınıf \_memeli, \_MammalSuperclass, ve \_nesne.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-166">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>  
  
 <span data-ttu-id="dbfa0-167">Örneğin, aşağıdaki .NET sınıf göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="dbfa0-167">For example, consider the following .NET class:</span></span>  
  
```vb  
' Applies the ClassInterfaceAttribute to set the interface to dual.  
<ClassInterface(ClassInterfaceType.AutoDual)> _  
' Implicitly extends System.Object.  
Public Class Mammal  
    Sub Eat()  
    Sub Breathe()  
    Sub Sleep()  
End Class  
```  
  
```csharp  
// Applies the ClassInterfaceAttribute to set the interface to dual.  
[ClassInterface(ClassInterfaceType.AutoDual)]  
// Implicitly extends System.Object.  
public class Mammal  
{  
    void  Eat();  
    void  Breathe():  
    void  Sleep();  
}  
```  
  
 <span data-ttu-id="dbfa0-168">COM istemcisi adlı bir sınıf arabirimi için bir işaretçi edinebilirsiniz `_Mammal`, Tür Kitaplığı'nda açıklanan, [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) aracı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-168">The COM client can obtain a pointer to a class interface named `_Mammal`, which is described in the type library that the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) tool generates.</span></span> <span data-ttu-id="dbfa0-169">Varsa `Mammal` sınıfı uygulanan bir veya daha fazla arabirimin, arabirimler coclass'ı altında görünür.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-169">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>  
  
```  
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]  
interface _Mammal : IDispatch  
{  
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*  
        pRetVal);  
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]  
        VARIANT_BOOL* pRetVal);  
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);  
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);  
    [id(0x6002000d)] HRESULT Eat();  
    [id(0x6002000e)] HRESULT Breathe();  
    [id(0x6002000f)] HRESULT Sleep();  
}  
[uuid(…)]  
coclass Mammal   
{  
    [default] interface _Mammal;  
}  
```  
  
 <span data-ttu-id="dbfa0-170">Sınıf arabirimi oluşturma isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-170">Generating the class interface is optional.</span></span> <span data-ttu-id="dbfa0-171">Varsayılan olarak, COM birlikte çalışma için bir tür kitaplığı dışarı her sınıf için bir yalnızca gönderme arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-171">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="dbfa0-172">Engellemek ya da bu arabirimi otomatik olarak oluşturulmasını uygulayarak değiştirmek <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> sınıfınıza.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-172">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="dbfa0-173">Yönetilen sınıflar com'da gösterme görev sınıf arabirimi kolaylaştırabilir rağmen kullanımları sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-173">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="dbfa0-174">Sınıf arabirimi kullanarak, açıkça, kendi tanımlama yerine yönetilen sınıfınızın gelecekteki sürüm karmaşık hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-174">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="dbfa0-175">Sınıf arabirimi kullanmadan önce aşağıdaki yönergeleri okuyun.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-175">Please read the following guidelines before using the class interface.</span></span>  
  
### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="dbfa0-176">COM istemcileri sınıf arabirimi oluşturmak yerine kullanmak için açık bir arabirim tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-176">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>  
 <span data-ttu-id="dbfa0-177">COM birlikte çalışma sınıf arabirimi otomatik olarak oluşturduğundan, sonrası sürüm değişiklikleri sınıfınıza ortak dil çalışma zamanı tarafından kullanıma sunulan sınıfı arabiriminin düzenini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-177">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="dbfa0-178">COM istemcileri bir arabirim düzeninde değişiklikler işlemek genellikle hazırlıksız olduğundan, sınıf üyesi düzenini değiştirirseniz, bunlar bölün.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-178">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>  
  
 <span data-ttu-id="dbfa0-179">Bu kılavuz, COM istemcileri için sunulan arabirimleri değiştirilemez kalması gereken kavram eklenir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-179">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="dbfa0-180">COM istemcileri yanlışlıkla arabirimi düzeni sıralayarak çiğnemekten riskini azaltmak için tüm değişiklikleri açıkça arabirimleri tanımlayarak sınıfa arabirimi düzeninden yalıtma.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-180">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>  
  
 <span data-ttu-id="dbfa0-181">Kullanım **ClassInterfaceAttribute** sınıf arabirimi otomatik olarak oluşturulmasını disengage ve aşağıdaki kod parçası gösterildiği gibi sınıf için açık bir arabirim uygulamak için:</span><span class="sxs-lookup"><span data-stu-id="dbfa0-181">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>  
  
```vb  
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp  
    Implements IExplicit  
    Sub M() Implements IExplicit.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.None)]  
public class LoanApp : IExplicit {  
    void M();  
}  
```  
  
 <span data-ttu-id="dbfa0-182">**ClassInterfaceType.None** değer sınıfı meta veriler için bir tür kitaplığı dışarı aktardığınızda oluşturulan sınıf arabirimi engeller.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-182">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="dbfa0-183">Önceki örnekte, COM istemcileri erişebilir `LoanApp` yalnızca aracılığıyla sınıf `IExplicit` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-183">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>  
  
### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="dbfa0-184">Gönderme tanımlayıcıları (DISPID değerleri) önbelleğe alma kaçının</span><span class="sxs-lookup"><span data-stu-id="dbfa0-184">Avoid caching dispatch identifiers (DispIds)</span></span>
 <span data-ttu-id="dbfa0-185">Sınıf arabirimi kullanarak, komut dosyası kullanan istemciler, Microsoft Visual Basic 6.0 istemciler veya arabirim üyelerinin DISPID değerleri önbelleğe almaz herhangi geç bağlama istemci için kabul edilebilir bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-185">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="dbfa0-186">Geç bağlama etkinleştirmek için arabirim üyeleri DISPID değerleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-186">DispIds identify interface members to enable late binding.</span></span>  
  
 <span data-ttu-id="dbfa0-187">Sınıf arabirimi için arabirim üye konumda DISPID değerleri nesil dayanır.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-187">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="dbfa0-188">Üye sırasını değiştirirseniz ve sınıf için bir tür kitaplığı dışarı aktarma, sınıf arabiriminde oluşturulan DISPID değerleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-188">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>  
  
 <span data-ttu-id="dbfa0-189">Geç bağlama COM istemcileri sınıf arabirimi kullanılırken çiğnemekten kaçının uygulamak **ClassInterfaceAttribute** ile **ClassInterfaceType.AutoDispatch** değeri.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-189">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="dbfa0-190">Bu değer yalnızca gönderme sınıfı arabirimini uygulayan ancak tür kitaplığı arabirimi açıklamasından atlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-190">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="dbfa0-191">Bir arabirim açıklaması istemciler DISPID değerleri, derleme zamanı önbelleğine erişemiyor.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-191">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="dbfa0-192">Bu sınıf arabirimi için varsayılan arabirim türü olsa da, öznitelik değeri açıkça uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-192">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>  
  
```vb  
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp  
    Implements IAnother  
    Sub M() Implements IAnother.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.AutoDispatch]  
public class LoanApp : IAnother {  
    void M();  
}  
```  
  
 <span data-ttu-id="dbfa0-193">Çalışma zamanında arabirim üyesini DISPID almak için COM istemcileri çağırabilirsiniz **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-193">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="dbfa0-194">Arabirimdeki bir yöntemi çağırmak için bağımsız değişken olarak döndürülen DISPID geçirmek **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-194">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>  
  
### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="dbfa0-195">Sınıf arabirimi için çift arabirim seçeneği kullanılarak kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-195">Restrict using the dual interface option for the class interface.</span></span>  
 <span data-ttu-id="dbfa0-196">Çift arabirimler arabirim üyeleri COM istemcileri tarafından erken ve geç bağlama etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-196">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="dbfa0-197">Tasarım zamanında ve test sırasında sınıf arabirimi için çift ayarlamak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-197">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="dbfa0-198">Yönetilen bir sınıfın (ve temel sınıflarından), hiçbir zaman olacaktır değiştirilmiş, bu da kabul edilebilir bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-198">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="dbfa0-199">Diğer durumlarda, sınıf arabirimi çift ayarlamamaya özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-199">In all other cases, avoid setting the class interface to dual.</span></span>  
  
 <span data-ttu-id="dbfa0-200">Otomatik olarak oluşturulan bir çift arabirim nadir durumlarda uygun olabilir; Ancak, daha sık bu sürümüyle ilgili karmaşıklık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-200">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="dbfa0-201">Örneğin, bir türetilmiş sınıfta sınıfı arabirimini kullanarak COM istemcileri için temel sınıf kolayca değişikliklerle bozulabilir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-201">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="dbfa0-202">Bir üçüncü taraf temel sınıf sağlar sınıfı arabiriminin düzenini dışında denetiminiz olur.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-202">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="dbfa0-203">Daha fazla, yalnızca gönderme arabirimi çift arabirim (**ClassInterface.AutoDual**) verilen tür kitaplığı sınıfı arabiriminde açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-203">Further, unlike a dispatch-only interface, a dual interface (**ClassInterface.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="dbfa0-204">Bu tür bir açıklama önbellek DISPID değerleri geç bağlama istemcilere çalışma zamanında önerir.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-204">Such a description encourages late-bound clients to cache DispIds at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbfa0-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbfa0-205">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [<span data-ttu-id="dbfa0-206">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="dbfa0-206">COM Wrappers</span></span>](com-wrappers.md)  
 [<span data-ttu-id="dbfa0-207">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="dbfa0-207">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="dbfa0-208">Birlikte Çalışma için .NET Türlerini Niteleme</span><span class="sxs-lookup"><span data-stu-id="dbfa0-208">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)  
 [<span data-ttu-id="dbfa0-209">Çalışma Zamanında Çağrılabilir Sarmalayıcı</span><span class="sxs-lookup"><span data-stu-id="dbfa0-209">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)