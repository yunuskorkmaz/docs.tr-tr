---
title: COM Aranabilir Sarmalayıcısı
ms.date: 10/23/2018
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
ms.openlocfilehash: 6f2f4055a95dbcea8d7872b5c5fa3ccede8c2c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400381"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="6bb4b-102">COM Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="6bb4b-102">COM Callable Wrapper</span></span>

<span data-ttu-id="6bb4b-103">Bir COM istemcisi bir .NET nesnesi aradığında, ortak dil çalışma süresi yönetilen nesneyi ve nesne için com çağrılabilir sarıcı (CCW) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="6bb4b-104">Bir .NET nesnesine doğrudan başvuruyapamayan COM istemcileri, yönetilen nesne için CCW'yi proxy olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="6bb4b-105">Çalışma süresi, hizmetlerini isteyen COM istemcilerinin sayısına bakılmaksızın yönetilen bir nesne için tam olarak bir CCW oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="6bb4b-106">Aşağıdaki resimde de görüldüğü gibi, birden çok COM istemcisi, INew arabirimini ortaya çıkaran CCW'ye bir başvuru tutabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="6bb4b-107">CCW, sırayla, arabirimi uygulayan yönetilen nesneye tek bir başvuru tutar ve toplanan çöp.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="6bb4b-108">Hem COM hem de .NET istemcileri aynı yönetilen nesne üzerinde aynı anda istekte bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![INew'ı ortaya çıkaran CCW'ye referans tutan birden çok COM istemcisi.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="6bb4b-110">COM çağrılabilir sarmalayıcılar .NET çalışma süresi içinde çalışan diğer sınıflar için görünmez.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-110">COM callable wrappers are invisible to other classes running within the .NET runtime.</span></span> <span data-ttu-id="6bb4b-111">Birincil amaçları yönetilen ve yönetilmeyen kod arasındaki aramaları mareşal etmektir; ancak, CCW'ler de sardıkları yönetilen nesnelerin nesne kimliğini ve nesne yaşam ömrünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="6bb4b-112">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bb4b-112">Object Identity</span></span>

<span data-ttu-id="6bb4b-113">Çalışma zamanı, .NET nesnesi için bellek ayırır ve çalışma zamanının nesneyi gerektiği gibi bellekte hareket ettirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="6bb4b-114">Buna karşılık, çalışma süresi, CCW için toplanan olmayan bir yığından bellek ayırır ve COM istemcilerinin sarıcıya doğrudan başvurmasını mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="6bb4b-115">Nesne Yaşam Süresi</span><span class="sxs-lookup"><span data-stu-id="6bb4b-115">Object Lifetime</span></span>

<span data-ttu-id="6bb4b-116">Sarar .NET istemcisinin aksine, CCW geleneksel COM modasında referans sayılır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="6bb4b-117">CCW'deki başvuru sayısı sıfıra ulaştığında, sarıcı başvuruyu yönetilen nesne üzerinde serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="6bb4b-118">Sonraki çöp toplama döngüsü sırasında, kalan başvuruları olmayan yönetilen bir nesne toplanır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="6bb4b-119">COM arayüzlerini simüle etme</span><span class="sxs-lookup"><span data-stu-id="6bb4b-119">Simulating COM interfaces</span></span>

<span data-ttu-id="6bb4b-120">CCW, com istemcilerine tüm ortak, COM görünür arabirimleri, veri türleri ve döndürme değerlerini, COM'un arabirim tabanlı etkileşimuygulamasıyla tutarlı bir şekilde ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="6bb4b-121">Bir COM istemcisi için,.NET nesnesi üzerinde yöntemleri çağırmak, COM nesnesindeki yöntemleri çağırmakla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-121">For a COM client, invoking methods on a .NET object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="6bb4b-122">Bu sorunsuz yaklaşımı oluşturmak için CCW, **IUnknown** ve **IDispatch**gibi geleneksel COM arabirimleri üretmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="6bb4b-123">Aşağıdaki resimde gösterildiği gibi, CCW sarar .NET nesnesi üzerinde tek bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="6bb4b-124">Hem COM istemcisi hem de .NET nesnesi CCW'nin proxy ve saplama yapısı aracılığıyla birbirleriyle etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![CCW'nin COM arabirimlerini nasıl ürettiğini gösteren diyagram.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="6bb4b-126">Yönetilen ortamda bir sınıf tarafından açıkça uygulanan arabirimleri ortaya çıkarmanın yanı sıra, .NET çalışma zamanı nesne adına aşağıdaki tabloda listelenen COM arabirimlerinin uygulamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET runtime supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="6bb4b-127">Bir .NET sınıfı, bu arabirimlerin kendi uygulamasını sağlayarak varsayılan davranışı geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="6bb4b-128">Ancak, çalışma zamanı her zaman **IUnknown** ve **IDispatch** arabirimleri için uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="6bb4b-129">Arabirim</span><span class="sxs-lookup"><span data-stu-id="6bb4b-129">Interface</span></span>|<span data-ttu-id="6bb4b-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bb4b-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6bb4b-131">**ıdispatch**</span><span class="sxs-lookup"><span data-stu-id="6bb4b-131">**IDispatch**</span></span>|<span data-ttu-id="6bb4b-132">Türüne geç bağlama için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="6bb4b-133">**ıerrorınfo**</span><span class="sxs-lookup"><span data-stu-id="6bb4b-133">**IErrorInfo**</span></span>|<span data-ttu-id="6bb4b-134">Hatanın, kaynağının, Yardım dosyasının, Yardım bağlamının ve hatayı tanımlayan arabirimin GUID'sinin (her zaman .NET sınıfları için **GUID_NULL)** metinsel bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="6bb4b-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="6bb4b-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="6bb4b-136">COM istemcilerinin yönetilen bir sınıf tarafından uygulanan **ITypeInfo** arabirimine erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span> <span data-ttu-id="6bb4b-137">COM'dan alınmayan türler için .NET Core'da döner. `COR_E_NOTSUPPORTED`</span><span class="sxs-lookup"><span data-stu-id="6bb4b-137">Returns `COR_E_NOTSUPPORTED` on .NET Core for types not imported from COM.</span></span> |
|<span data-ttu-id="6bb4b-138">**ısupporterrorınfo**</span><span class="sxs-lookup"><span data-stu-id="6bb4b-138">**ISupportErrorInfo**</span></span>|<span data-ttu-id="6bb4b-139">Yönetilen nesnenin **IErrorInfo** arabirimini destekleyip desteklemediğini belirlemek için bir COM istemcisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-139">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="6bb4b-140">Bu nedenle, istemci nin en son özel durum nesnesine bir işaretçi almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-140">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="6bb4b-141">Yönetilen tüm türler **IErrorInfo** arabirimini destekler.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-141">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="6bb4b-142">**ITypeInfo** (Sadece.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="6bb4b-142">**ITypeInfo** (.NET Framework Only)</span></span>|<span data-ttu-id="6bb4b-143">Tlbexp.exe tarafından üretilen tür bilgileriyle tam olarak aynı olan bir sınıf için tür bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-143">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="6bb4b-144">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="6bb4b-144">**IUnknown**</span></span>|<span data-ttu-id="6bb4b-145">COM istemcisinin CCW'nin ömrünü yönettiği ve tür zorlamasağladığı **IUnknown** arabiriminin standart uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-145">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="6bb4b-146">Yönetilen bir sınıf, aşağıdaki tabloda açıklanan COM arabirimlerini de sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-146">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="6bb4b-147">Arabirim</span><span class="sxs-lookup"><span data-stu-id="6bb4b-147">Interface</span></span>|<span data-ttu-id="6bb4b-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bb4b-148">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6bb4b-149">(\_*Sınıf adı*) sınıf arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bb4b-149">The (\_*classname*) class interface</span></span>|<span data-ttu-id="6bb4b-150">Yönetilen bir nesne üzerinde açıkça açıkta kalan tüm ortak arabirimleri, yöntemleri, özellikleri ve alanları ortaya çıkaran, çalışma zamanı tarafından açıkta kalan ve açıkça tanımlanmamış arabirim.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-150">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="6bb4b-151">**IConnectionPoint** ve **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="6bb4b-151">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="6bb4b-152">Temsilci tabanlı olaylara kaynak sağlayan nesneler için arabirim (olay abonelerini kaydetmek için bir arabirim).</span><span class="sxs-lookup"><span data-stu-id="6bb4b-152">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="6bb4b-153">**IDispatchEx** (.NET Framework Only)</span><span class="sxs-lookup"><span data-stu-id="6bb4b-153">**IDispatchEx** (.NET Framework Only)</span></span>|<span data-ttu-id="6bb4b-154">Sınıf **IExpando'yu**uyguluyorsa çalışma zamanı tarafından sağlanan arabirim.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-154">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="6bb4b-155">**IDispatchEx** arabirimi, **IDispatch'in**aksine, üyelerin numaralandırma, ekleme, silme ve büyük/küçük harf duyarlı aramalarına olanak tanıyan **IDispatch** arabiriminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-155">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="6bb4b-156">**ıenumvarıant**</span><span class="sxs-lookup"><span data-stu-id="6bb4b-156">**IEnumVARIANT**</span></span>|<span data-ttu-id="6bb4b-157">Sınıf **Ayrılmaz**uygularsa koleksiyondaki nesneleri sayısalhale getiren koleksiyon türü sınıflar için arabirim.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-157">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="6bb4b-158">Sınıf arabirimini tanıtma</span><span class="sxs-lookup"><span data-stu-id="6bb4b-158">Introducing the class interface</span></span>

<span data-ttu-id="6bb4b-159">Yönetilen kodda açıkça tanımlanmayan sınıf arabirimi, .NET nesnesinde açıkça açık tabir edilen tüm ortak yöntemleri, özellikleri, alanları ve olayları ortaya çıkaran bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-159">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="6bb4b-160">Bu arabirim, yalnızca çift veya yalnızca göndere gönderilen bir arabirim olabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-160">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="6bb4b-161">Sınıf arabirimi, bir alt alt skorun öncesinde .NET sınıfının adını alır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-161">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="6bb4b-162">Örneğin, sınıf Memeliler için sınıf \_arabirimi Memeli'dir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-162">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="6bb4b-163">Türemiş sınıflar için sınıf arabirimi, taban sınıfın tüm ortak yöntemlerini, özelliklerini ve alanlarını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-163">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="6bb4b-164">Türetilen sınıf, her taban sınıf için bir sınıf arabirimi de ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-164">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="6bb4b-165">Örneğin, sınıf Memeli sinifini genişletirse, kendisi System.Object' i genişletir, .NET \_nesnesi COM istemcilerine Memeli, \_MemeliSuperclass ve \_Nesne adlIkiüç sınıf arabirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-165">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="6bb4b-166">Örneğin, aşağıdaki .NET sınıfını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6bb4b-166">For example, consider the following .NET class:</span></span>

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
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

<span data-ttu-id="6bb4b-167">COM istemcisi adlı `_Mammal`bir sınıf arabirimi için bir işaretçi elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-167">The COM client can obtain a pointer to a class interface named `_Mammal`.</span></span> <span data-ttu-id="6bb4b-168">.NET Framework'de, arayüz tanımını içeren bir tür kitaplığı oluşturmak için Tür `_Mammal` [Kitaplığı İhracatçısı (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-168">On .NET Framework, you can use the [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) tool to generate a type library containing the `_Mammal` interface definition.</span></span> <span data-ttu-id="6bb4b-169">Tip Kitaplığı İhracatçısı .NET Core'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-169">The Type Library Exporter is not supported on .NET Core.</span></span> <span data-ttu-id="6bb4b-170">`Mammal` Sınıf bir veya daha fazla arabirim uyguladıysa, arabirimler ortak sınıfın altında görünür.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-170">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

```console
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

<span data-ttu-id="6bb4b-171">Sınıf arabiriminin oluşturması isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-171">Generating the class interface is optional.</span></span> <span data-ttu-id="6bb4b-172">Varsayılan olarak, COM interop bir tür kitaplığı için dışa aktardığınız her sınıf için yalnızca gönderme arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-172">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="6bb4b-173">Sınıfınıza uygulayarak <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> bu arabirimin otomatik oluşturulmasını engelleyebilir veya değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-173">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="6bb4b-174">Sınıf arabirimi yönetilen sınıfları COM'a maruz bırakma görevini kolaylaştırsa da, kullanımları sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-174">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="6bb4b-175">Sınıf arabirimini kullanmak, kendi sınıfınızı açıkça tanımlamak yerine yönetilen sınıfınuzun gelecekteki sürümünü zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-175">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="6bb4b-176">Sınıf arabirimini kullanmadan önce lütfen aşağıdaki yönergeleri okuyun.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-176">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="6bb4b-177">Sınıf arabirimi oluşturmak yerine COM istemcilerinin kullanması için açık bir arabirim tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-177">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="6bb4b-178">COM interop otomatik olarak bir sınıf arabirimi oluşturduğundan, sınıfınızdaki sürüm sonrası değişiklikler, ortak dil çalışma zamanı tarafından açığa çıkarılan sınıf arabiriminin düzenini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-178">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="6bb4b-179">COM istemcileri genellikle arabirimin düzenindeki değişiklikleri işlemek için hazır olmadığından, sınıfın üye düzenini değiştirirseniz kırılırlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-179">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="6bb4b-180">Bu kılavuz, COM istemcilerine maruz kalan arabirimlerin değiştirilemez kalması gerektiği fikrini güçlendirmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-180">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="6bb4b-181">Arabirim düzenini yanlışlıkla yeniden sıralayarak COM istemcilerini kırma riskini azaltmak için, arabirimleri açıkça tanımlayarak sınıfdaki tüm değişiklikleri arabirim düzeninden yalıtın.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-181">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="6bb4b-182">Sınıf arabiriminin otomatik neslini devre dışı bırakıp, aşağıdaki kod parçasının gösterdiği gibi sınıf için açık bir arabirim uygulamak için **ClassInterfaceAtöz'ü** kullanın:</span><span class="sxs-lookup"><span data-stu-id="6bb4b-182">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

<span data-ttu-id="6bb4b-183">**ClassInterfaceType.None** değeri, sınıf meta verileri bir tür kitaplığına dışa aktarıldığında sınıf arabiriminin oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-183">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="6bb4b-184">Önceki örnekte, COM istemcileri `LoanApp` sınıfa yalnızca `IExplicit` arabirim üzerinden erişebilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-184">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="6bb4b-185">Sevk tanımlayıcılarını (DispIds) önbelleğe almaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="6bb4b-185">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="6bb4b-186">Sınıf arabirimini kullanmak, komut dosyası istemcileri, Microsoft Visual Basic 6.0 istemcileri veya arabirim üyelerinin DispId'lerini önbelleğe alamayan herhangi bir geç bağlantı istemcisi için kabul edilebilir bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-186">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="6bb4b-187">DispIds geç bağlama sağlamak için arabirim üyelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-187">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="6bb4b-188">Sınıf arabirimi için, DispIds oluşturma arabirimde üyenin konumuna dayanır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-188">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="6bb4b-189">Üyenin sırasını değiştirir ve sınıfı bir tür kitaplığına dışa aktarırsanız, sınıf arabiriminde oluşturulan DispId'leri değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-189">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="6bb4b-190">Sınıf arabirimini kullanırken geç bağlanan COM istemcilerini kırmamak için **ClassInterfaceType.AutoDispatch** değeriyle **ClassInterfaceAttribute** uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-190">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="6bb4b-191">Bu değer yalnızca gönderilen sınıf arabirimi uygular, ancak tür kitaplığından arabirim açıklamasını atlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-191">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="6bb4b-192">Arabirim açıklaması olmadan, istemciler Derleme zamanında DispId'leri önbelleğe alamıyor.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-192">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="6bb4b-193">Bu sınıf arabirimi için varsayılan arabirim türü olsa da, öznitelik değerini açıkça uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-193">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

<span data-ttu-id="6bb4b-194">Çalışma zamanında bir arayüz üyesinin DispId almak için, COM **istemcileri IDispatch.GetIdsOfNames**arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-194">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="6bb4b-195">Arabirimde bir yöntem çağırmak için, döndürülen DispId'i bağımsız değişken olarak **IDispatch.Invoke'a geçirin.**</span><span class="sxs-lookup"><span data-stu-id="6bb4b-195">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="6bb4b-196">Sınıf arabirimi için çift arabirim seçeneğini kullanarak kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-196">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="6bb4b-197">Çift arabirimler, COM istemcileri tarafından arayüz üyelerine erken ve geç bağlanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-197">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="6bb4b-198">Tasarım zamanında ve sınama sırasında, sınıf arabirimini çift olarak ayarlamayı yararlı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-198">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="6bb4b-199">Hiçbir zaman değiştirilmeyecek yönetilen bir sınıf (ve temel sınıfları) için bu seçenek de kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-199">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="6bb4b-200">Diğer tüm durumlarda, sınıf arabirimini çift olarak ayarlamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-200">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="6bb4b-201">Otomatik olarak oluşturulan çift arabirim nadir durumlarda uygun olabilir; ancak, daha sık sürümle ilgili karmaşıklık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-201">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="6bb4b-202">Örneğin, türetilmiş bir sınıfın sınıf arabirimini kullanan COM istemcileri taban sınıfdeğişiklikleriyle kolayca kırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-202">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="6bb4b-203">Üçüncü bir taraf taban sınıfı sağladığında, sınıf arabiriminin düzeni sizin denetiminiz dışındadır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-203">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="6bb4b-204">Ayrıca, yalnızca gönderilen bir arabirimin aksine, çift arabirim **(ClassInterfaceType.AutoDual)** dışa aktarılan tür kitaplığında sınıf arabiriminin açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-204">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="6bb4b-205">Böyle bir açıklama, geç giden istemcileri derleme zamanında DispId'leri önbelleğe almaya teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-205">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="6bb4b-206">Tüm COM olay bildirimlerinin geç olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-206">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="6bb4b-207">Varsayılan olarak, COM türü bilgileri doğrudan yönetilen derlemelere gömülür ve bu da birincil interop derlemeleri (PI'ler) gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-207">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="6bb4b-208">Ancak, katıştırılmış tür bilgilerinin sınırlamalarından biri, COM olay bildirimlerinin erken bağlanan vtable çağrıları `IDispatch::Invoke` tarafından teslimini desteklememesi, yalnızca geç gelen çağrıları desteklemesidir.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-208">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="6bb4b-209">Uygulamanız COM olay arabirimi yöntemlerine erken çağrı gerektiriyorsa, Visual Studio'daki `true` **Embed Interop Types** özelliğini Visual Studio'da ayarlayabilir veya proje dosyanıza aşağıdaki öğeyi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6bb4b-209">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="6bb4b-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bb4b-210">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="6bb4b-211">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="6bb4b-211">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="6bb4b-212">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="6bb4b-212">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="6bb4b-213">.NET Core Bileşenlerini COM’da Gösterme</span><span class="sxs-lookup"><span data-stu-id="6bb4b-213">Exposing .NET Core Components to COM</span></span>](../../core/native-interop/expose-components-to-com.md)
- [<span data-ttu-id="6bb4b-214">Birlikte Çalışma için Niteleyici .NET Türleri</span><span class="sxs-lookup"><span data-stu-id="6bb4b-214">Qualifying .NET Types for Interoperation</span></span>](qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="6bb4b-215">Çalışma Zamanı Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="6bb4b-215">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
