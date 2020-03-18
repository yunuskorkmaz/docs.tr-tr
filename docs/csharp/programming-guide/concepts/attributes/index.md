---
title: Öznitelikler (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 2a07035ea97bb0ff1a8f4793fe8a30d3a42c34a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399751"
---
# <a name="attributes-c"></a><span data-ttu-id="a5ecc-102">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="a5ecc-102">Attributes (C#)</span></span>

<span data-ttu-id="a5ecc-103">Öznitelikler, meta verileri veya bildirimsel bilgileri kodla (derlemeler, türler, yöntemler, özellikler vb.) ilişkilendirme güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="a5ecc-104">Bir öznitelik bir program varlığı ile ilişkilendirildikten sonra, öznitelik *yansıma*adı verilen bir teknik kullanılarak çalışma zamanında sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="a5ecc-105">Daha fazla bilgi için [Yansıma (C#)](../reflection.md)'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="a5ecc-106">Özniteliklerin aşağıdaki özellikleri vardır:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="a5ecc-107">Öznitelikler programınıza meta veri ekler.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="a5ecc-108">*Meta veriler,* bir programda tanımlanan türler hakkında bilgidir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="a5ecc-109">Tüm .NET derlemeleri, derlemede tanımlanan tür ve tür üyelerini açıklayan belirli bir meta veri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="a5ecc-110">Gerekli olan ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="a5ecc-111">Daha fazla bilgi için bkz: [Özel Öznitelikler oluşturma (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a5ecc-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="a5ecc-112">Sınıflar ve özellikler gibi tüm derlemelere, modüllere veya daha küçük program öğelerine bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="a5ecc-113">Öznitelikler, bağımsız değişkenleri yöntem ve özelliklerle aynı şekilde kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="a5ecc-114">Programınız yansımayı kullanarak kendi meta verilerini veya diğer programlardaki meta verileri inceleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="a5ecc-115">Daha fazla bilgi için bkz: [Yansıma (C#) kullanarak Özniteliklere Erişim.](accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="a5ecc-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="a5ecc-116">Öznitelikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="a5ecc-116">Using attributes</span></span>

<span data-ttu-id="a5ecc-117">Öznitelikler çoğu bildirime yerleştirilebilir, ancak belirli bir öznitelik geçerli olduğu bildirim türlerini kısıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="a5ecc-118">C#'da, öznitelik adını kare ayraçlarla ([]) uygulandığı varlığın bildiriminin üzerine koyarak bir öznitelik belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="a5ecc-119">Bu örnekte, <xref:System.SerializableAttribute> öznitelik bir sınıfa belirli bir özellik uygulamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="a5ecc-120">Öznitelik <xref:System.Runtime.InteropServices.DllImportAttribute> içeren bir yöntem aşağıdaki örnek gibi bildirilir:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="a5ecc-121">Aşağıdaki örnekte görüldüğü gibi bir bildirime birden fazla öznitelik yerleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="a5ecc-122">Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="a5ecc-123">Böyle bir çok kullanımlı öznitelik bir <xref:System.Diagnostics.ConditionalAttribute>örnek:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="a5ecc-124">Kural kuralına göre, tüm öznitelik adları .NET kitaplıklarındaki diğer öğelerden ayırt etmek için "Öznitelik" sözcüğüyle sona erer.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="a5ecc-125">Ancak, kodözleri kullanırken öznitelik soneki belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="a5ecc-126">Örneğin, `[DllImport]` `[DllImportAttribute]`.NET `DllImportAttribute` Framework Class Kitaplığı'ndaki özniteliğin gerçek adıdır.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="a5ecc-127">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="a5ecc-127">Attribute parameters</span></span>

<span data-ttu-id="a5ecc-128">Birçok öznitelik, konumsal, adsız veya adlandırılmış parametrelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="a5ecc-129">Herhangi bir konumsal parametreler belirli bir sırada belirtilmelidir ve atlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="a5ecc-130">Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="a5ecc-131">Önce pozisyonparametreleri belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-131">Positional parameters are specified first.</span></span> <span data-ttu-id="a5ecc-132">Örneğin, bu üç öznitelik eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="a5ecc-133">İlk parametre, DLL adı, konumsal ve her zaman önce gelir; diğerleri ne adlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="a5ecc-134">Bu durumda, her iki adlandırılmış parametre varsayılan false, bu yüzden atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="a5ecc-135">Konumsal parametreler öznitelik oluşturucu parametrelerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="a5ecc-136">Adlandırılmış veya isteğe bağlı parametreler özniteliğin özelliklerine veya alanlarına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="a5ecc-137">Varsayılan parametre değerleri hakkında bilgi almak için tek tek özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="a5ecc-138">Öznitelik hedefleri</span><span class="sxs-lookup"><span data-stu-id="a5ecc-138">Attribute targets</span></span>

<span data-ttu-id="a5ecc-139">Bir özniteliğin *hedefi,* özniteliğin uygulandığı varlıktır.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="a5ecc-140">Örneğin, bir öznitelik bir sınıf, belirli bir yöntem veya tüm derleme için geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="a5ecc-141">Varsayılan olarak, onu izleyen öğeye bir öznitelik uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-141">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="a5ecc-142">Ancak, örneğin bir öznitelik bir yönteme mi, parametresine mi yoksa geri dönüş değerine mi uygulandığını açıkça belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="a5ecc-143">Bir öznitelik hedefini açıkça tanımlamak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="a5ecc-144">Olası `target` değerlerin listesi aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="a5ecc-145">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="a5ecc-145">Target value</span></span>|<span data-ttu-id="a5ecc-146">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="a5ecc-147">Tüm montaj</span><span class="sxs-lookup"><span data-stu-id="a5ecc-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="a5ecc-148">Geçerli montaj modülü</span><span class="sxs-lookup"><span data-stu-id="a5ecc-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="a5ecc-149">Bir sınıftaki veya yapıdaki alan</span><span class="sxs-lookup"><span data-stu-id="a5ecc-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="a5ecc-150">Olay</span><span class="sxs-lookup"><span data-stu-id="a5ecc-150">Event</span></span>|
|`method`|<span data-ttu-id="a5ecc-151">Yöntem `get` veya `set` özellik erişime erişim</span><span class="sxs-lookup"><span data-stu-id="a5ecc-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="a5ecc-152">Yöntem parametreleri veya `set` özellik aksesuar parametreleri</span><span class="sxs-lookup"><span data-stu-id="a5ecc-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="a5ecc-153">Özellik</span><span class="sxs-lookup"><span data-stu-id="a5ecc-153">Property</span></span>|
|`return`|<span data-ttu-id="a5ecc-154">Yöntemin, özellik dizinicisinin `get` veya özellik erişime erişiminin iade değeri</span><span class="sxs-lookup"><span data-stu-id="a5ecc-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="a5ecc-155">Yapı, sınıf, arayüz, enum veya temsilci</span><span class="sxs-lookup"><span data-stu-id="a5ecc-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="a5ecc-156">Otomatik olarak `field` uygulanan bir özellik için oluşturulan destek alanına bir öznitelik uygulamak için hedef değeri [belirtirsiniz.](../../../properties.md)</span><span class="sxs-lookup"><span data-stu-id="a5ecc-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="a5ecc-157">Aşağıdaki örnek, öznitelikleri derlemelere ve modüllere nasıl uygulayacağımızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="a5ecc-158">Daha fazla bilgi için [Ortak Öznitelikler (C#)](common-attributes.md)'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="a5ecc-159">Aşağıdaki örnek, C#'daki yöntemlere, yöntem parametrelerine ve yöntem döndürme değerlerine öznitelikleri nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="a5ecc-160">Geçerli olarak tanımlanan hedeflere `ValidatedContract` bakılmaksızın, yalnızca `return` döndürme değerleri için uygulanacak `ValidatedContract` şekilde tanımlanmış olsa bile hedefin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="a5ecc-161">Başka bir deyişle, derleyici `AttributeUsage` belirsiz öznitelik hedeflerini çözmek için bilgileri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="a5ecc-162">Daha fazla bilgi için [Bkz. AttributeUsage (C#)](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="a5ecc-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="a5ecc-163">Öznitelikler için ortak kullanımlar</span><span class="sxs-lookup"><span data-stu-id="a5ecc-163">Common uses for attributes</span></span>

<span data-ttu-id="a5ecc-164">Aşağıdaki liste, koddaki özniteliklerin ortak kullanımlarından birkaçını içerir:</span><span class="sxs-lookup"><span data-stu-id="a5ecc-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="a5ecc-165">Yöntemin SOAP `WebMethod` protokolü üzerinden çağrılabilir olması gerektiğini belirtmek için Web hizmetlerinde özniteliği kullanarak işaretleme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="a5ecc-166">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="a5ecc-167">Yerel kodla birlikte çalışırken yöntem parametrelerinin nasıl sıralanır olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="a5ecc-168">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="a5ecc-169">Sınıflar, yöntemler ve arabirimler için COM özelliklerini açıklayan.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="a5ecc-170"><xref:System.Runtime.InteropServices.DllImportAttribute> Sınıfı kullanarak yönetilmeyen kodu çağırma.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="a5ecc-171">Derlemenizi başlık, sürüm, açıklama veya ticari marka açısından açıklama.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="a5ecc-172">Bir sınıfın hangi üyelerinin kalıcılık için seri hale getirmek için açıklanması.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="a5ecc-173">XML serileştirme için sınıf üyeleri ve XML düğümleri arasında nasıl eşleneceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="a5ecc-174">Yöntemler için güvenlik gereksinimlerini açıklayan.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="a5ecc-175">Güvenliği zorlamak için kullanılan özellikleri belirtme.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="a5ecc-176">Kodun hata ayıklanması kolay kalması için optimizasyonları tam zamanında (JIT) derleyicitarafından denetler.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="a5ecc-177">Bir yönteme arayan hakkında bilgi edinme.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a5ecc-178">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="a5ecc-178">Related sections</span></span>

<span data-ttu-id="a5ecc-179">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-179">For more information, see:</span></span>

- [<span data-ttu-id="a5ecc-180">Özel Öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="a5ecc-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="a5ecc-181">Yansıma (C#) kullanarak Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="a5ecc-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="a5ecc-182">Öznitelikleri kullanarak C/C++ birleşimoluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="a5ecc-182">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="a5ecc-183">Ortak Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="a5ecc-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="a5ecc-184">Arayan Bilgileri (C#)</span><span class="sxs-lookup"><span data-stu-id="a5ecc-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="a5ecc-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5ecc-185">See also</span></span>

- [<span data-ttu-id="a5ecc-186">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a5ecc-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="a5ecc-187">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="a5ecc-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="a5ecc-188">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a5ecc-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="a5ecc-189">C'de Öznitelikleri Kullanma #</span><span class="sxs-lookup"><span data-stu-id="a5ecc-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
