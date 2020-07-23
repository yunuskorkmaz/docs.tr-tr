---
title: Öznitelikler (C#)
description: Meta verileri veya bildirim temelli bilgileri C# ' deki kodla ilişkilendirmek için öznitelikleri kullanmayı öğrenin. Bir öznitelik, yansıma kullanılarak çalışma zamanında sorgulanabilir.
ms.date: 04/26/2018
ms.openlocfilehash: 5c57838b649531d8e8fe89919771adf8830e7f54
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924991"
---
# <a name="attributes-c"></a><span data-ttu-id="58508-104">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="58508-104">Attributes (C#)</span></span>

<span data-ttu-id="58508-105">Öznitelikler, meta verileri veya bildirime dayalı bilgilerin kod (derlemeler, türler, Yöntemler, özellikler, vb.) ile ilişkilendirilmesi için güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="58508-105">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="58508-106">Bir öznitelik bir program varlığıyla ilişkilendirildikten sonra, çalışma zamanında, *yansıma*adlı bir teknik kullanarak öznitelik sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="58508-106">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="58508-107">Daha fazla bilgi için bkz. [yansıma (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="58508-107">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="58508-108">Öznitelikler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="58508-108">Attributes have the following properties:</span></span>

- <span data-ttu-id="58508-109">Öznitelikler, programınıza meta veri ekler.</span><span class="sxs-lookup"><span data-stu-id="58508-109">Attributes add metadata to your program.</span></span> <span data-ttu-id="58508-110">*Meta veriler* , bir programda tanımlanan türlerle ilgili bilgiler.</span><span class="sxs-lookup"><span data-stu-id="58508-110">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="58508-111">Tüm .NET derlemeleri, derlemede tanımlanan türleri ve tür üyelerini açıklayan, belirtilen meta veri kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="58508-111">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="58508-112">Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58508-112">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="58508-113">Daha fazla bilgi için bkz. [özel öznitelikler oluşturma (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="58508-113">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="58508-114">Tüm derlemeler, modüller veya sınıflar ve özellikler gibi daha küçük program öğelerine bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58508-114">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="58508-115">Öznitelikler bağımsız değişkenleri Yöntemler ve özelliklerle aynı şekilde kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="58508-115">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="58508-116">Programınız, yansıma kullanarak kendi meta verilerini veya diğer programlardaki meta verileri inceleyebilir.</span><span class="sxs-lookup"><span data-stu-id="58508-116">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="58508-117">Daha fazla bilgi için bkz. [yansıma kullanarak özniteliklere erişme (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="58508-117">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="58508-118">Öznitelikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="58508-118">Using attributes</span></span>

<span data-ttu-id="58508-119">Öznitelikler, her bir bildirime yerleştirilebilecek, ancak belirli bir öznitelik, geçerli olduğu bildirimlerin türlerini kısıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="58508-119">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="58508-120">C# ' de, geçerli olduğu varlık bildiriminin üstüne köşeli ayraç ([]) içine alınmış özniteliğin adını yerleştirerek bir özniteliği belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58508-120">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="58508-121">Bu örnekte, <xref:System.SerializableAttribute> özniteliği bir sınıfa belirli bir özelliği uygulamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="58508-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="58508-122">Özniteliğine sahip bir yöntem <xref:System.Runtime.InteropServices.DllImportAttribute> Aşağıdaki örnekte olduğu gibi bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="58508-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="58508-123">Aşağıdaki örnekte gösterildiği gibi, bir bildirime birden fazla öznitelik yerleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="58508-123">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="58508-124">Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="58508-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="58508-125">Bu tür bir çok kullanım özniteliğine örnek <xref:System.Diagnostics.ConditionalAttribute> :</span><span class="sxs-lookup"><span data-stu-id="58508-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="58508-126">Kurala göre, tüm öznitelik adları, bunları .NET kitaplıklarında diğer öğelerden ayırt etmek için "Attribute" kelimesiyle biter.</span><span class="sxs-lookup"><span data-stu-id="58508-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="58508-127">Ancak, koddaki öznitelikleri kullanırken öznitelik sonekini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="58508-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="58508-128">Örneğin, `[DllImport]` ile eşdeğerdir `[DllImportAttribute]` , ancak `DllImportAttribute` .NET sınıf kitaplığındaki özniteliğin gerçek adıdır.</span><span class="sxs-lookup"><span data-stu-id="58508-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="58508-129">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="58508-129">Attribute parameters</span></span>

<span data-ttu-id="58508-130">Birçok özniteliğin, konumsal, adlandırılmamış veya adlandırılmış olabilecek parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="58508-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="58508-131">Herhangi bir Konumsal parametre belirli bir sırada belirtilmelidir ve atlanamaz.</span><span class="sxs-lookup"><span data-stu-id="58508-131">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="58508-132">Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="58508-132">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="58508-133">Konumsal parametreler önce belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="58508-133">Positional parameters are specified first.</span></span> <span data-ttu-id="58508-134">Örneğin, bu üç öznitelik eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="58508-134">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="58508-135">İlk parametre olan DLL adı, konumsal ve her zaman ilk olarak gelir; diğerleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="58508-135">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="58508-136">Bu durumda, her ikisi de varsayılan olarak false değerine sahiptir, bu nedenle bu parametreler atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="58508-136">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="58508-137">Konumsal parametreler öznitelik oluşturucusunun parametrelerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="58508-137">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="58508-138">Adlandırılmış ya da isteğe bağlı parametreler, özelliğin özelliklerine veya alanlarına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="58508-138">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="58508-139">Varsayılan parametre değerleri hakkında bilgi için bağımsız özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="58508-139">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="58508-140">Öznitelik hedefleri</span><span class="sxs-lookup"><span data-stu-id="58508-140">Attribute targets</span></span>

<span data-ttu-id="58508-141">Bir özniteliğin *hedefi* , özniteliğin uygulandığı varlıktır.</span><span class="sxs-lookup"><span data-stu-id="58508-141">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="58508-142">Örneğin, bir öznitelik bir sınıfa, belirli bir yönteme veya bir derlemenin tamamına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="58508-142">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="58508-143">Varsayılan olarak, bir öznitelik, onu izleyen öğesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="58508-143">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="58508-144">Ancak, bir özniteliğin bir yönteme mi, yoksa parametresine mi, yoksa dönüş değerine mi uygulanacağını de açıkça belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58508-144">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="58508-145">Bir öznitelik hedefini açıkça tanımlamak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="58508-145">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="58508-146">Olası `target` değerler listesi aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="58508-146">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="58508-147">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="58508-147">Target value</span></span>|<span data-ttu-id="58508-148">Şunlara uygulanır</span><span class="sxs-lookup"><span data-stu-id="58508-148">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="58508-149">Tüm derleme</span><span class="sxs-lookup"><span data-stu-id="58508-149">Entire assembly</span></span>|
|`module`|<span data-ttu-id="58508-150">Geçerli derleme modülü</span><span class="sxs-lookup"><span data-stu-id="58508-150">Current assembly module</span></span>|
|`field`|<span data-ttu-id="58508-151">Bir sınıf veya yapı içindeki alan</span><span class="sxs-lookup"><span data-stu-id="58508-151">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="58508-152">Olay</span><span class="sxs-lookup"><span data-stu-id="58508-152">Event</span></span>|
|`method`|<span data-ttu-id="58508-153">Yöntem veya `get` ve `set` özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="58508-153">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="58508-154">Yöntem parametreleri veya `set` özellik erişimcisi parametreleri</span><span class="sxs-lookup"><span data-stu-id="58508-154">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="58508-155">Özellik</span><span class="sxs-lookup"><span data-stu-id="58508-155">Property</span></span>|
|`return`|<span data-ttu-id="58508-156">Metodun, özellik dizin oluşturucusunun veya `get` özellik erişimcisinin dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="58508-156">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="58508-157">Struct, Class, Interface, Enum veya Delegate</span><span class="sxs-lookup"><span data-stu-id="58508-157">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="58508-158">`field` [Otomatik uygulanan bir özellik](../../../properties.md)için oluşturulan yedekleme alanına bir öznitelik uygulamak için hedef değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="58508-158">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="58508-159">Aşağıdaki örnek, derlemeler ve modüllere özniteliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="58508-159">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="58508-160">Daha fazla bilgi için bkz. [ortak öznitelikler (C#)](../../../language-reference/attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="58508-160">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="58508-161">Aşağıdaki örnek, C# ' deki yöntemlere, yöntem parametrelerine ve yöntem dönüş değerlerine özniteliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="58508-161">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="58508-162">Üzerinde geçerli olarak tanımlanan hedeflerin ne olursa olsun `ValidatedContract` , `return` `ValidatedContract` yalnızca dönüş değerleri için geçerli olarak tanımlansa bile hedefin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="58508-162">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="58508-163">Diğer bir deyişle, derleyici `AttributeUsage` belirsiz öznitelik hedeflerini çözümlemek için bilgileri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="58508-163">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="58508-164">Daha fazla bilgi için bkz. [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span><span class="sxs-lookup"><span data-stu-id="58508-164">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="58508-165">Öznitelikler için ortak kullanımlar</span><span class="sxs-lookup"><span data-stu-id="58508-165">Common uses for attributes</span></span>

<span data-ttu-id="58508-166">Aşağıdaki listede, kod içindeki özniteliklerin yaygın kullanımları yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="58508-166">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="58508-167">`WebMethod`YÖNTEMIN SOAP protokolü üzerinden çağrılabilir olması gerektiğini göstermek Için Web hizmetlerindeki özniteliği kullanılarak yöntemleri işaretleme.</span><span class="sxs-lookup"><span data-stu-id="58508-167">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="58508-168">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="58508-168">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="58508-169">Yerel kodla birlikte çalışırken yöntem parametrelerinin nasıl hazırlanacağını açıklama.</span><span class="sxs-lookup"><span data-stu-id="58508-169">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="58508-170">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="58508-170">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="58508-171">Sınıflar, Yöntemler ve arabirimler için COM özelliklerini açıklama.</span><span class="sxs-lookup"><span data-stu-id="58508-171">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="58508-172">Sınıfını kullanarak yönetilmeyen kodu çağırma <xref:System.Runtime.InteropServices.DllImportAttribute> .</span><span class="sxs-lookup"><span data-stu-id="58508-172">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="58508-173">Derlemenizi başlık, sürüm, açıklama veya ticari marka açısından açıklama.</span><span class="sxs-lookup"><span data-stu-id="58508-173">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="58508-174">Bir sınıfın kalıcılığı için hangi üyelerin serileştirmek gerektiğini açıklama.</span><span class="sxs-lookup"><span data-stu-id="58508-174">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="58508-175">XML ile serileştirme için sınıf üyeleri ve XML düğümleri arasında nasıl eşleme yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="58508-175">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="58508-176">Yöntemler için güvenlik gereksinimlerini açıklama.</span><span class="sxs-lookup"><span data-stu-id="58508-176">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="58508-177">Güvenliği zorlamak için kullanılan özellikleri belirtme.</span><span class="sxs-lookup"><span data-stu-id="58508-177">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="58508-178">Tam zamanında (JıT) derleyicisine yönelik iyileştirmeler denetleniyor, böylece kod hata ayıklama için kolay kalır.</span><span class="sxs-lookup"><span data-stu-id="58508-178">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="58508-179">Bir yönteme arayan hakkında bilgi alma.</span><span class="sxs-lookup"><span data-stu-id="58508-179">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="58508-180">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="58508-180">Related sections</span></span>

<span data-ttu-id="58508-181">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="58508-181">For more information, see:</span></span>

- [<span data-ttu-id="58508-182">Özel öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="58508-182">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="58508-183">Yansıma kullanarak özniteliklere erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="58508-183">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="58508-184">Öznitelikleri kullanarak C/C++ birleşimi oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="58508-184">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="58508-185">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="58508-185">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="58508-186">Arayan bilgileri (C#)</span><span class="sxs-lookup"><span data-stu-id="58508-186">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="58508-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58508-187">See also</span></span>

- [<span data-ttu-id="58508-188">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="58508-188">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="58508-189">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="58508-189">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="58508-190">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="58508-190">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="58508-191">C 'de öznitelikleri kullanma #</span><span class="sxs-lookup"><span data-stu-id="58508-191">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
