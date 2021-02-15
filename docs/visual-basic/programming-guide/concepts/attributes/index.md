---
description: 'Daha fazla bilgi edinin: özniteliklere genel bakış (Visual Basic)'
title: Özniteliklere genel bakış
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: f25e69452f0af1c89af667619e673f8906704d1f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437728"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="80250-103">Özniteliklere genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80250-103">Attributes overview (Visual Basic)</span></span>

<span data-ttu-id="80250-104">Öznitelikler, meta verileri veya bildirime dayalı bilgilerin kod (derlemeler, türler, Yöntemler, özellikler, vb.) ile ilişkilendirilmesi için güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="80250-104">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="80250-105">Bir öznitelik bir program varlığıyla ilişkilendirildikten sonra, çalışma zamanında, *yansıma* adlı bir teknik kullanarak öznitelik sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="80250-105">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="80250-106">Daha fazla bilgi için bkz. [yansıma (Visual Basic)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="80250-106">For more information, see [Reflection (Visual Basic)](../reflection.md).</span></span>

<span data-ttu-id="80250-107">Öznitelikler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="80250-107">Attributes have the following properties:</span></span>

- <span data-ttu-id="80250-108">Öznitelikler, programınıza meta veri ekler.</span><span class="sxs-lookup"><span data-stu-id="80250-108">Attributes add metadata to your program.</span></span> <span data-ttu-id="80250-109">*Meta veriler* , bir programda tanımlanan türlerle ilgili bilgiler.</span><span class="sxs-lookup"><span data-stu-id="80250-109">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="80250-110">Tüm .NET derlemeleri, derlemede tanımlanan türleri ve tür üyelerini açıklayan, belirtilen meta veri kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="80250-110">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="80250-111">Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80250-111">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="80250-112">Daha fazla bilgi için bkz. [özel öznitelikler oluşturma (Visual Basic)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="80250-112">For more information, see, [Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md).</span></span>

- <span data-ttu-id="80250-113">Tüm derlemeler, modüller veya sınıflar ve özellikler gibi daha küçük program öğelerine bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80250-113">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>

- <span data-ttu-id="80250-114">Öznitelikler bağımsız değişkenleri Yöntemler ve özelliklerle aynı şekilde kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="80250-114">Attributes can accept arguments in the same way as methods and properties.</span></span>

- <span data-ttu-id="80250-115">Programınız, yansıma kullanarak kendi meta verilerini veya diğer programlardaki meta verileri inceleyebilir.</span><span class="sxs-lookup"><span data-stu-id="80250-115">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="80250-116">Daha fazla bilgi için bkz. [yansıma kullanarak özniteliklere erişme (Visual Basic)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="80250-116">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="80250-117">Öznitelikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="80250-117">Using Attributes</span></span>

<span data-ttu-id="80250-118">Öznitelikler, her bir bildirime yerleştirilebilecek, ancak belirli bir öznitelik, geçerli olduğu bildirimlerin türlerini kısıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="80250-118">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="80250-119">Visual Basic, bir öznitelik açılı ayraçlar () içine alınır \< > .</span><span class="sxs-lookup"><span data-stu-id="80250-119">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="80250-120">Aynı satırda, uygulandığı öğeden hemen önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="80250-120">It must appear immediately before the element to which it is applied, on the same line.</span></span>

<span data-ttu-id="80250-121">Bu örnekte, <xref:System.SerializableAttribute> özniteliği bir sınıfa belirli bir özelliği uygulamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="80250-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

```vb
<System.Serializable()> Public Class SampleClass
    ' Objects of this type can be serialized.
End Class
```

 <span data-ttu-id="80250-122">Özniteliğine sahip bir yöntem <xref:System.Runtime.InteropServices.DllImportAttribute> şöyle bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="80250-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
<System.Runtime.InteropServices.DllImport("user32.dll")>
Sub SampleMethod()
End Sub
```

<span data-ttu-id="80250-123">Bir bildirime birden fazla öznitelik yerleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="80250-123">More than one attribute can be placed on a declaration:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
Sub MethodA(<[In](), Out()> ByVal x As Double)
End Sub
Sub MethodB(<Out(), [In]()> ByVal x As Double)
End Sub
```

<span data-ttu-id="80250-124">Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="80250-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="80250-125">Bu tür bir çok kullanım özniteliğine örnek <xref:System.Diagnostics.ConditionalAttribute> :</span><span class="sxs-lookup"><span data-stu-id="80250-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

```vb
<Conditional("DEBUG"), Conditional("TEST1")>
Sub TraceMethod()
End Sub
```

> [!NOTE]
> <span data-ttu-id="80250-126">Kurala göre, tüm öznitelik adları, .NET Framework diğer öğelerden ayırt edilebilmesi için "Attribute" kelimesiyle biter.</span><span class="sxs-lookup"><span data-stu-id="80250-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="80250-127">Ancak, koddaki öznitelikleri kullanırken öznitelik sonekini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="80250-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="80250-128">Örneğin, `[DllImport]` öğesine eşdeğerdir `[DllImportAttribute]` , ancak `DllImportAttribute` .NET Framework özniteliğin gerçek adıdır.</span><span class="sxs-lookup"><span data-stu-id="80250-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="80250-129">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="80250-129">Attribute Parameters</span></span>

<span data-ttu-id="80250-130">Birçok özniteliğin, konumsal, adlandırılmamış veya adlandırılmış olabilecek parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="80250-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="80250-131">Herhangi bir Konumsal parametre belirli bir sırada belirtilmelidir ve atlanamaz; Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="80250-131">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="80250-132">Konumsal parametreler önce belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="80250-132">Positional parameters are specified first.</span></span> <span data-ttu-id="80250-133">Örneğin, bu üç öznitelik eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="80250-133">For example, these three attributes are equivalent:</span></span>

```vb
<DllImport("user32.dll")>
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>
```

<span data-ttu-id="80250-134">İlk parametre olan DLL adı, konumsal ve her zaman ilk olarak gelir; diğerleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="80250-134">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="80250-135">Bu durumda, her ikisi de varsayılan olarak false değerine sahiptir, bu nedenle bu parametreler atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="80250-135">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="80250-136">Varsayılan parametre değerleri hakkında bilgi için bağımsız özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="80250-136">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="80250-137">Öznitelik Hedefleri</span><span class="sxs-lookup"><span data-stu-id="80250-137">Attribute Targets</span></span>

<span data-ttu-id="80250-138">Bir özniteliğin *hedefi* , özniteliğin uygulandığı varlıktır.</span><span class="sxs-lookup"><span data-stu-id="80250-138">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="80250-139">Örneğin, bir öznitelik bir sınıfa, belirli bir yönteme veya bir derlemenin tamamına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="80250-139">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="80250-140">Varsayılan olarak, bir öznitelik, kendisinden önce gelen öğe için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="80250-140">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="80250-141">Ancak, bir özniteliğin bir yönteme mi, yoksa parametresine mi, yoksa dönüş değerine mi uygulanacağını de açıkça belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80250-141">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="80250-142">Bir öznitelik hedefini açıkça tanımlamak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="80250-142">To explicitly identify an attribute target, use the following syntax:</span></span>

```vb
<target : attribute-list>
```

<span data-ttu-id="80250-143">Olası `target` değerler listesi aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="80250-143">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="80250-144">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="80250-144">Target value</span></span>|<span data-ttu-id="80250-145">Şunlara uygulanır</span><span class="sxs-lookup"><span data-stu-id="80250-145">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="80250-146">Tüm derleme</span><span class="sxs-lookup"><span data-stu-id="80250-146">Entire assembly</span></span>|
|`module`|<span data-ttu-id="80250-147">Geçerli derleme modülü (bir Visual Basic modülünden farklı)</span><span class="sxs-lookup"><span data-stu-id="80250-147">Current assembly module (which is different from a Visual Basic Module)</span></span>|

 <span data-ttu-id="80250-148">Aşağıdaki örnek, derlemeler ve modüllere özniteliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="80250-148">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="80250-149">Daha fazla bilgi için bkz. [ortak öznitelikler (Visual Basic)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="80250-149">For more information, see [Common Attributes (Visual Basic)](common-attributes.md).</span></span>

```vb
Imports System.Reflection
<Assembly: AssemblyTitleAttribute("Production assembly 4"),
Module: CLSCompliant(True)>
```

## <a name="common-uses-for-attributes"></a><span data-ttu-id="80250-150">Öznitelikler için ortak kullanımlar</span><span class="sxs-lookup"><span data-stu-id="80250-150">Common Uses for Attributes</span></span>

<span data-ttu-id="80250-151">Aşağıdaki listede, kod içindeki özniteliklerin yaygın kullanımları yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="80250-151">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="80250-152">`WebMethod`YÖNTEMIN SOAP protokolü üzerinden çağrılabilir olması gerektiğini göstermek Için Web hizmetlerindeki özniteliği kullanılarak yöntemleri işaretleme.</span><span class="sxs-lookup"><span data-stu-id="80250-152">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="80250-153">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="80250-153">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>

- <span data-ttu-id="80250-154">Yerel kodla birlikte çalışırken yöntem parametrelerinin nasıl hazırlanacağını açıklama.</span><span class="sxs-lookup"><span data-stu-id="80250-154">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="80250-155">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="80250-155">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

- <span data-ttu-id="80250-156">Sınıflar, Yöntemler ve arabirimler için COM özelliklerini açıklama.</span><span class="sxs-lookup"><span data-stu-id="80250-156">Describing the COM properties for classes, methods, and interfaces.</span></span>

- <span data-ttu-id="80250-157">Sınıfını kullanarak yönetilmeyen kodu çağırma <xref:System.Runtime.InteropServices.DllImportAttribute> .</span><span class="sxs-lookup"><span data-stu-id="80250-157">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>

- <span data-ttu-id="80250-158">Derlemenizi başlık, sürüm, açıklama veya ticari marka açısından açıklama.</span><span class="sxs-lookup"><span data-stu-id="80250-158">Describing your assembly in terms of title, version, description, or trademark.</span></span>

- <span data-ttu-id="80250-159">Bir sınıfın kalıcılığı için hangi üyelerin serileştirmek gerektiğini açıklama.</span><span class="sxs-lookup"><span data-stu-id="80250-159">Describing which members of a class to serialize for persistence.</span></span>

- <span data-ttu-id="80250-160">XML ile serileştirme için sınıf üyeleri ve XML düğümleri arasında nasıl eşleme yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="80250-160">Describing how to map between class members and XML nodes for XML serialization.</span></span>

- <span data-ttu-id="80250-161">Yöntemler için güvenlik gereksinimlerini açıklama.</span><span class="sxs-lookup"><span data-stu-id="80250-161">Describing the security requirements for methods.</span></span>

- <span data-ttu-id="80250-162">Güvenliği zorlamak için kullanılan özellikleri belirtme.</span><span class="sxs-lookup"><span data-stu-id="80250-162">Specifying characteristics used to enforce security.</span></span>

- <span data-ttu-id="80250-163">Tam zamanında (JıT) derleyicisine yönelik iyileştirmeler denetleniyor, böylece kod hata ayıklama için kolay kalır.</span><span class="sxs-lookup"><span data-stu-id="80250-163">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>

- <span data-ttu-id="80250-164">Bir yönteme arayan hakkında bilgi alma.</span><span class="sxs-lookup"><span data-stu-id="80250-164">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="80250-165">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="80250-165">Related Sections</span></span>

<span data-ttu-id="80250-166">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="80250-166">For more information, see:</span></span>

- [<span data-ttu-id="80250-167">Özel öznitelikler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80250-167">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)

- [<span data-ttu-id="80250-168">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80250-168">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)

- [<span data-ttu-id="80250-169">Nasıl yapılır: öznitelikleri kullanarak C/C++ birleşimi oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80250-169">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)

- [<span data-ttu-id="80250-170">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80250-170">Common Attributes (Visual Basic)</span></span>](common-attributes.md)

- [<span data-ttu-id="80250-171">Arayan bilgileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80250-171">Caller Information (Visual Basic)</span></span>](../caller-information.md)

## <a name="see-also"></a><span data-ttu-id="80250-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80250-172">See also</span></span>

- [<span data-ttu-id="80250-173">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="80250-173">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="80250-174">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80250-174">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="80250-175">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80250-175">Attributes</span></span>](../../../../standard/attributes/index.md)
