---
title: Öznitelikler (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 42a7035a9dae146ad7a303da41c83891e5e19ef8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668620"
---
# <a name="attributes-c"></a><span data-ttu-id="8c3a0-102">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="8c3a0-102">Attributes (C#)</span></span>

<span data-ttu-id="8c3a0-103">Öznitelikler (derlemeler, türler, yöntemler, özellikler ve benzeri) koduyla ilişkili bir meta veriler ya da tanımlayıcı bilgileri, güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="8c3a0-104">Öznitelik, bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında olarak adlandırılan tekniği kullanarak sorgulanabilir *yansıma*.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="8c3a0-105">Daha fazla bilgi için [yansıma (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="8c3a0-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="8c3a0-106">Öznitelik, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="8c3a0-107">Öznitelik meta verileri programınıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="8c3a0-108">*Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="8c3a0-109">Tüm .NET derlemeleri derlemede tanımlanan tür üyeleri ve türleri açıklayan meta veriler belirtilen bir kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="8c3a0-110">Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="8c3a0-111">Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8c3a0-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="8c3a0-112">Tüm derlemeler, modüller veya daha küçük program öğelerini sınıfları ve özellikleri gibi bir veya daha fazla öznitelikleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="8c3a0-113">Öznitelikleri yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="8c3a0-114">Programınızı kendi meta veriler ya da diğer programları meta verilerde yansıma kullanarak inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="8c3a0-115">Daha fazla bilgi için [yansıma (C#) kullanarak erişen özniteliklerle](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="8c3a0-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="8c3a0-116">Öznitelikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="8c3a0-116">Using attributes</span></span>

<span data-ttu-id="8c3a0-117">Belirli bir öznitelik bildirimleri, geçerli olduğu türlerini kısıtlamak ancak öznitelikleri pek çok bildiriminde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="8c3a0-118">İçinde C#, bir öznitelik adı köşeli ayraç ([]) içine özniteliği yerleştirerek, geçerli varlık bildiriminin üstüne belirttiğiniz.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="8c3a0-119">Bu örnekte, <xref:System.SerializableAttribute> özniteliği, belirli bir özellik için bir sınıf uygulamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="8c3a0-120">Özniteliğine sahip metot <xref:System.Runtime.InteropServices.DllImportAttribute> aşağıdaki gibi bildirilir:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="8c3a0-121">Birden fazla özniteliği aşağıdaki örnekte gösterildiği gibi bildiriminde yerleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="8c3a0-122">Bazı öznitelikleri kereden fazla belirli bir varlık için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="8c3a0-123">Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="8c3a0-124">Kural gereği, tüm öznitelik adları .NET kitaplıklarına diğer öğelerden bunları ayırt etmek için "özniteliği" sözcüğü ile biter.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="8c3a0-125">Ancak, öznitelikler kodda kullanıldığında özniteliği soneki belirtmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="8c3a0-126">Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework Sınıf Kitaplığı'nda özniteliğin gerçek adıdır.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="8c3a0-127">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="8c3a0-127">Attribute parameters</span></span>

<span data-ttu-id="8c3a0-128">Konumsal, adlandırılmamış veya adlandırılmış parametreleri fazla öznitelik var.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="8c3a0-129">Konumsal parametreleri, belirli bir sırayla belirtilmelidir ve atlanamaz.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="8c3a0-130">Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="8c3a0-131">Konumsal parametreler ilk belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-131">Positional parameters are specified first.</span></span> <span data-ttu-id="8c3a0-132">Örneğin, bu üç özniteliğin eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="8c3a0-133">İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğerleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="8c3a0-134">Bu durumda, döngülerinden çıkarılabilir şekilde her ikisi de false olarak parametreleri varsayılan adı.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="8c3a0-135">Konumsal parametreler öznitelik oluşturucunun parametrelere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="8c3a0-136">Adlandırılmış ya da isteğe bağlı parametre için özellikler veya alanları özniteliğinin karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="8c3a0-137">Varsayılan parametre değerleri hakkında bilgi için tek bir özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="8c3a0-138">Öznitelik hedefleri</span><span class="sxs-lookup"><span data-stu-id="8c3a0-138">Attribute targets</span></span>

<span data-ttu-id="8c3a0-139">*Hedef* bir öznitelik varlığı özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="8c3a0-140">Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="8c3a0-141">Varsayılan olarak, kendisinden öğe için bir özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-141">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="8c3a0-142">Ancak, bir yöntem veya, parametre veya dönüş değeri bir öznitelik uygulanmış olup olmadığını açıkça, örneğin, belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="8c3a0-143">Bir öznitelik hedefi açıkça tanımlamak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="8c3a0-144">Olası listesini `target` değerleri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="8c3a0-145">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="8c3a0-145">Target value</span></span>|<span data-ttu-id="8c3a0-146">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="8c3a0-147">Tüm derleme</span><span class="sxs-lookup"><span data-stu-id="8c3a0-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="8c3a0-148">Geçerli derleme Modülü</span><span class="sxs-lookup"><span data-stu-id="8c3a0-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="8c3a0-149">Bir sınıf veya yapı alanı</span><span class="sxs-lookup"><span data-stu-id="8c3a0-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="8c3a0-150">Olay</span><span class="sxs-lookup"><span data-stu-id="8c3a0-150">Event</span></span>|
|`method`|<span data-ttu-id="8c3a0-151">Yöntem veya `get` ve `set` özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="8c3a0-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="8c3a0-152">Yöntem parametreleri veya `set` özelliği erişimcisi parametreleri</span><span class="sxs-lookup"><span data-stu-id="8c3a0-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="8c3a0-153">Özellik</span><span class="sxs-lookup"><span data-stu-id="8c3a0-153">Property</span></span>|
|`return`|<span data-ttu-id="8c3a0-154">Bir yöntem, özellik dizinleyicisi, değeri döndürür veya `get` özellik erişimcisi</span><span class="sxs-lookup"><span data-stu-id="8c3a0-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="8c3a0-155">Yapı, sınıf, arabirim, enum veya temsilci</span><span class="sxs-lookup"><span data-stu-id="8c3a0-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="8c3a0-156">Belirtirsiniz `field` destek alanı için bir öznitelik uygulamak için hedef değer için oluşturulan bir [otomatik uygulanan özellik](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="8c3a0-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="8c3a0-157">Aşağıdaki örnek, derlemeler ve modüller için öznitelik uygulayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="8c3a0-158">Daha fazla bilgi için [ortak öznitelikler (C#)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8c3a0-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="8c3a0-159">Aşağıdaki örnekte, yöntem, yöntem parametreleri, öznitelikleri uygulamak gösterilmiştir ve yöntem dönüş değerleri C# dilinde.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="8c3a0-160">Hedeflerde bakılmaksızın `ValidatedContract` geçerli olması için tanımlanan `return` hedef sahip belirtilmesi bile `ValidatedContract` yalnızca dönüş değerleri uygulamak için tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="8c3a0-161">Diğer bir deyişle, derleyici kullanmaz `AttributeUsage` bilgileri belirsiz öznitelik hedefleri çözümlemek için.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="8c3a0-162">Daha fazla bilgi için [AttributeUsage (C#)](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="8c3a0-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="8c3a0-163">Öznitelikler için yaygın kullanımları</span><span class="sxs-lookup"><span data-stu-id="8c3a0-163">Common uses for attributes</span></span>

<span data-ttu-id="8c3a0-164">Aşağıdaki liste, kod öznitelikleri'nın yaygın kullanımları birkaçını içerir:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="8c3a0-165">Yöntemlerini kullanarak işaretleme `WebMethod` Web Hizmetleri yöntemi SOAP protokolü üzerinden çağrılabilmelidir belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="8c3a0-166">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="8c3a0-167">Yerel kod ile birlikte çalışırken yöntem parametreleri'ı sıralama nasıl açıklayan.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="8c3a0-168">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="8c3a0-169">Sınıfları, yöntemleri ve arabirimleri için COM özelliklerini açıklayan.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="8c3a0-170">Yönetilmeyen çağırma kod kullanarak <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="8c3a0-171">Başlık, sürüm, açıklama veya ticari marka açısından derlemenizi açıklayan.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="8c3a0-172">Kalıcılık için seri hale getirmek için bir sınıfın hangi üyelerinin açıklayan.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="8c3a0-173">Sınıf üyeleri için XML serileştirme XML düğümler arasındaki eşlemeyle ilgili bilgi açıklayan.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="8c3a0-174">Güvenlik gereksinimleri yöntemleri için açıklama.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="8c3a0-175">Güvenliği zorlamak için kullanılan özellikleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="8c3a0-176">Kod hatalarını ayıklamak kolay kalır. böylece en iyi duruma getirme just-in-time (JIT) derleyici tarafından denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="8c3a0-177">Bir yöntemin arayanı hakkında bilgi edinme.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8c3a0-178">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="8c3a0-178">Related sections</span></span>

<span data-ttu-id="8c3a0-179">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="8c3a0-179">For more information, see:</span></span>

- [<span data-ttu-id="8c3a0-180">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c3a0-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="8c3a0-181">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="8c3a0-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="8c3a0-182">Nasıl yapılır: Öznitelikleri kullanarak C/C++ birleşimi oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="8c3a0-182">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="8c3a0-183">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="8c3a0-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="8c3a0-184">Arayan bilgileri (C#)</span><span class="sxs-lookup"><span data-stu-id="8c3a0-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="8c3a0-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c3a0-185">See also</span></span>

- [<span data-ttu-id="8c3a0-186">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8c3a0-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="8c3a0-187">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="8c3a0-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="8c3a0-188">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8c3a0-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="8c3a0-189">Öznitelikleri kullanarak C#</span><span class="sxs-lookup"><span data-stu-id="8c3a0-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
