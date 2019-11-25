---
title: Öznitelikler (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 2a07035ea97bb0ff1a8f4793fe8a30d3a42c34a7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141557"
---
# <a name="attributes-c"></a><span data-ttu-id="11a80-102">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="11a80-102">Attributes (C#)</span></span>

<span data-ttu-id="11a80-103">Öznitelikler, meta verileri veya bildirime dayalı bilgilerin kod (derlemeler, türler, Yöntemler, özellikler, vb.) ile ilişkilendirilmesi için güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="11a80-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="11a80-104">Bir öznitelik bir program varlığıyla ilişkilendirildikten sonra, çalışma zamanında, *yansıma*adlı bir teknik kullanarak öznitelik sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="11a80-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="11a80-105">Daha fazla bilgi için bkz. [yansımaC#()](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="11a80-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="11a80-106">Öznitelikler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="11a80-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="11a80-107">Öznitelikler, programınıza meta veri ekler.</span><span class="sxs-lookup"><span data-stu-id="11a80-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="11a80-108">*Meta veriler* , bir programda tanımlanan türlerle ilgili bilgiler.</span><span class="sxs-lookup"><span data-stu-id="11a80-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="11a80-109">Tüm .NET derlemeleri, derlemede tanımlanan türleri ve tür üyelerini açıklayan, belirtilen meta veri kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="11a80-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="11a80-110">Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a80-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="11a80-111">Daha fazla bilgi için bkz. [özel öznitelikler (C#) oluşturma](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="11a80-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="11a80-112">Tüm derlemeler, modüller veya sınıflar ve özellikler gibi daha küçük program öğelerine bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a80-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="11a80-113">Öznitelikler bağımsız değişkenleri Yöntemler ve özelliklerle aynı şekilde kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="11a80-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="11a80-114">Programınız, yansıma kullanarak kendi meta verilerini veya diğer programlardaki meta verileri inceleyebilir.</span><span class="sxs-lookup"><span data-stu-id="11a80-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="11a80-115">Daha fazla bilgi için bkz. [Reflection (C#) kullanarak özniteliklere erişme](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="11a80-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="11a80-116">Öznitelikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="11a80-116">Using attributes</span></span>

<span data-ttu-id="11a80-117">Öznitelikler, her bir bildirime yerleştirilebilecek, ancak belirli bir öznitelik, geçerli olduğu bildirimlerin türlerini kısıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="11a80-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="11a80-118">' C#De, geçerli olduğu varlık bildiriminin üzerine köşeli ayraç ([]) içine alınmış özniteliğin adını yerleştirerek bir özniteliği belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a80-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="11a80-119">Bu örnekte, bir sınıfa belirli bir özelliği uygulamak için <xref:System.SerializableAttribute> özniteliği kullanılır:</span><span class="sxs-lookup"><span data-stu-id="11a80-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="11a80-120"><xref:System.Runtime.InteropServices.DllImportAttribute> özniteliğine sahip bir yöntem aşağıdaki örnekte olduğu gibi bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="11a80-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="11a80-121">Aşağıdaki örnekte gösterildiği gibi, bir bildirime birden fazla öznitelik yerleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="11a80-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="11a80-122">Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="11a80-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="11a80-123">Bu tür bir çok kullanım özniteliğine örnek <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="11a80-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="11a80-124">Kurala göre, tüm öznitelik adları, bunları .NET kitaplıklarında diğer öğelerden ayırt etmek için "Attribute" kelimesiyle biter.</span><span class="sxs-lookup"><span data-stu-id="11a80-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="11a80-125">Ancak, koddaki öznitelikleri kullanırken öznitelik sonekini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="11a80-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="11a80-126">Örneğin, `[DllImport]` `[DllImportAttribute]`eşdeğerdir, ancak `DllImportAttribute` özniteliğin .NET Framework sınıf kitaplığındaki gerçek adıdır.</span><span class="sxs-lookup"><span data-stu-id="11a80-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="11a80-127">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="11a80-127">Attribute parameters</span></span>

<span data-ttu-id="11a80-128">Birçok özniteliğin, konumsal, adlandırılmamış veya adlandırılmış olabilecek parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="11a80-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="11a80-129">Herhangi bir Konumsal parametre belirli bir sırada belirtilmelidir ve atlanamaz.</span><span class="sxs-lookup"><span data-stu-id="11a80-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="11a80-130">Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="11a80-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="11a80-131">Konumsal parametreler önce belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11a80-131">Positional parameters are specified first.</span></span> <span data-ttu-id="11a80-132">Örneğin, bu üç öznitelik eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="11a80-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="11a80-133">İlk parametre olan DLL adı, konumsal ve her zaman ilk olarak gelir; diğerleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="11a80-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="11a80-134">Bu durumda, her ikisi de varsayılan olarak false değerine sahiptir, bu nedenle bu parametreler atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="11a80-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="11a80-135">Konumsal parametreler öznitelik oluşturucusunun parametrelerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="11a80-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="11a80-136">Adlandırılmış ya da isteğe bağlı parametreler, özelliğin özelliklerine veya alanlarına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="11a80-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="11a80-137">Varsayılan parametre değerleri hakkında bilgi için bağımsız özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="11a80-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="11a80-138">Öznitelik hedefleri</span><span class="sxs-lookup"><span data-stu-id="11a80-138">Attribute targets</span></span>

<span data-ttu-id="11a80-139">Bir özniteliğin *hedefi* , özniteliğin uygulandığı varlıktır.</span><span class="sxs-lookup"><span data-stu-id="11a80-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="11a80-140">Örneğin, bir öznitelik bir sınıfa, belirli bir yönteme veya bir derlemenin tamamına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="11a80-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="11a80-141">Varsayılan olarak, bir öznitelik, onu izleyen öğesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="11a80-141">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="11a80-142">Ancak, bir özniteliğin bir yönteme mi, yoksa parametresine mi, yoksa dönüş değerine mi uygulanacağını de açıkça belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a80-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="11a80-143">Bir öznitelik hedefini açıkça tanımlamak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="11a80-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="11a80-144">Olası `target` değerleri listesi aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11a80-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="11a80-145">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="11a80-145">Target value</span></span>|<span data-ttu-id="11a80-146">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="11a80-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="11a80-147">Tüm derleme</span><span class="sxs-lookup"><span data-stu-id="11a80-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="11a80-148">Geçerli derleme modülü</span><span class="sxs-lookup"><span data-stu-id="11a80-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="11a80-149">Bir sınıf veya yapı içindeki alan</span><span class="sxs-lookup"><span data-stu-id="11a80-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="11a80-150">Olay</span><span class="sxs-lookup"><span data-stu-id="11a80-150">Event</span></span>|
|`method`|<span data-ttu-id="11a80-151">Yöntem veya `get` ve `set` Özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="11a80-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="11a80-152">Yöntem parametreleri veya `set` özellik erişimcisi parametreleri</span><span class="sxs-lookup"><span data-stu-id="11a80-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="11a80-153">Özellik</span><span class="sxs-lookup"><span data-stu-id="11a80-153">Property</span></span>|
|`return`|<span data-ttu-id="11a80-154">Metodun, özellik dizin oluşturucusunun veya `get` Özellik erişimcisinin dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="11a80-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="11a80-155">Struct, Class, Interface, Enum veya Delegate</span><span class="sxs-lookup"><span data-stu-id="11a80-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="11a80-156">[Otomatik uygulanan bir özellik](../../../properties.md)için oluşturulan yedekleme alanına bir öznitelik uygulamak üzere `field` Target değerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a80-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="11a80-157">Aşağıdaki örnek, derlemeler ve modüllere özniteliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11a80-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="11a80-158">Daha fazla bilgi için bkz. [ortak özniteliklerC#()](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="11a80-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="11a80-159">Aşağıdaki örnek, içindeki C#yöntemlere, yöntem parametrelerine ve yöntem dönüş değerlerine özniteliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11a80-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="11a80-160">`ValidatedContract` tanımlanan hedeflerden bağımsız olarak, `ValidatedContract` yalnızca dönüş değerleri uygulamak üzere tanımlansa bile `return` hedefi belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="11a80-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="11a80-161">Diğer bir deyişle, derleyici belirsiz öznitelik hedeflerini çözümlemek için `AttributeUsage` bilgilerini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="11a80-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="11a80-162">Daha fazla bilgi için bkz. [AttributeUsageC#()](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="11a80-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="11a80-163">Öznitelikler için ortak kullanımlar</span><span class="sxs-lookup"><span data-stu-id="11a80-163">Common uses for attributes</span></span>

<span data-ttu-id="11a80-164">Aşağıdaki listede, kod içindeki özniteliklerin yaygın kullanımları yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="11a80-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="11a80-165">Metodun SOAP protokolü üzerinden çağrılabilir olması gerektiğini göstermek için Web hizmetlerindeki `WebMethod` özniteliğini kullanarak yöntemleri işaretleme.</span><span class="sxs-lookup"><span data-stu-id="11a80-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="11a80-166">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="11a80-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="11a80-167">Yerel kodla birlikte çalışırken yöntem parametrelerinin nasıl hazırlanacağını açıklama.</span><span class="sxs-lookup"><span data-stu-id="11a80-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="11a80-168">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="11a80-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="11a80-169">Sınıflar, Yöntemler ve arabirimler için COM özelliklerini açıklama.</span><span class="sxs-lookup"><span data-stu-id="11a80-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="11a80-170">Yönetilmeyen kod <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfını kullanarak çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="11a80-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="11a80-171">Derlemenizi başlık, sürüm, açıklama veya ticari marka açısından açıklama.</span><span class="sxs-lookup"><span data-stu-id="11a80-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="11a80-172">Bir sınıfın kalıcılığı için hangi üyelerin serileştirmek gerektiğini açıklama.</span><span class="sxs-lookup"><span data-stu-id="11a80-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="11a80-173">XML ile serileştirme için sınıf üyeleri ve XML düğümleri arasında nasıl eşleme yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="11a80-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="11a80-174">Yöntemler için güvenlik gereksinimlerini açıklama.</span><span class="sxs-lookup"><span data-stu-id="11a80-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="11a80-175">Güvenliği zorlamak için kullanılan özellikleri belirtme.</span><span class="sxs-lookup"><span data-stu-id="11a80-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="11a80-176">Tam zamanında (JıT) derleyicisine yönelik iyileştirmeler denetleniyor, böylece kod hata ayıklama için kolay kalır.</span><span class="sxs-lookup"><span data-stu-id="11a80-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="11a80-177">Bir yönteme arayan hakkında bilgi alma.</span><span class="sxs-lookup"><span data-stu-id="11a80-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="11a80-178">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="11a80-178">Related sections</span></span>

<span data-ttu-id="11a80-179">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="11a80-179">For more information, see:</span></span>

- [<span data-ttu-id="11a80-180">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="11a80-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="11a80-181">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="11a80-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="11a80-182">Öznitelikleri kullanarak C/C++ Union oluşturma ()C#</span><span class="sxs-lookup"><span data-stu-id="11a80-182">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="11a80-183">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="11a80-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="11a80-184">Arayan bilgileri (C#)</span><span class="sxs-lookup"><span data-stu-id="11a80-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="11a80-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11a80-185">See also</span></span>

- [<span data-ttu-id="11a80-186">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="11a80-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="11a80-187">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="11a80-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="11a80-188">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11a80-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="11a80-189">İçindeki öznitelikleri kullanmaC#</span><span class="sxs-lookup"><span data-stu-id="11a80-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
