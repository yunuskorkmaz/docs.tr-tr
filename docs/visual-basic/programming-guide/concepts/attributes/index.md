---
title: Özniteliklere genel bakış
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: 97a2a13102718b6ee8829fca678b2b49df21e5d1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349489"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="239f1-102">Özniteliklere genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="239f1-102">Attributes overview (Visual Basic)</span></span>

<span data-ttu-id="239f1-103">Öznitelikler, meta verileri veya bildirime dayalı bilgilerin kod (derlemeler, türler, Yöntemler, özellikler, vb.) ile ilişkilendirilmesi için güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="239f1-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="239f1-104">Bir öznitelik bir program varlığıyla ilişkilendirildikten sonra, çalışma zamanında, *yansıma*adlı bir teknik kullanarak öznitelik sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="239f1-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="239f1-105">Daha fazla bilgi için bkz. [yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="239f1-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>

<span data-ttu-id="239f1-106">Öznitelikler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="239f1-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="239f1-107">Öznitelikler, programınıza meta veri ekler.</span><span class="sxs-lookup"><span data-stu-id="239f1-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="239f1-108">*Meta veriler* , bir programda tanımlanan türlerle ilgili bilgiler.</span><span class="sxs-lookup"><span data-stu-id="239f1-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="239f1-109">Tüm .NET derlemeleri, derlemede tanımlanan türleri ve tür üyelerini açıklayan, belirtilen meta veri kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="239f1-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="239f1-110">Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="239f1-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="239f1-111">Daha fazla bilgi için bkz. [özel öznitelikler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="239f1-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>

- <span data-ttu-id="239f1-112">Tüm derlemeler, modüller veya sınıflar ve özellikler gibi daha küçük program öğelerine bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="239f1-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>

- <span data-ttu-id="239f1-113">Öznitelikler bağımsız değişkenleri Yöntemler ve özelliklerle aynı şekilde kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="239f1-113">Attributes can accept arguments in the same way as methods and properties.</span></span>

- <span data-ttu-id="239f1-114">Programınız, yansıma kullanarak kendi meta verilerini veya diğer programlardaki meta verileri inceleyebilir.</span><span class="sxs-lookup"><span data-stu-id="239f1-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="239f1-115">Daha fazla bilgi için bkz. [yansıma kullanarak özniteliklere erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="239f1-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="239f1-116">Öznitelikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="239f1-116">Using Attributes</span></span>

<span data-ttu-id="239f1-117">Öznitelikler, her bir bildirime yerleştirilebilecek, ancak belirli bir öznitelik, geçerli olduğu bildirimlerin türlerini kısıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="239f1-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="239f1-118">Visual Basic, bir öznitelik açılı ayraçlar içine alınır (\< >).</span><span class="sxs-lookup"><span data-stu-id="239f1-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="239f1-119">Aynı satırda, uygulandığı öğeden hemen önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="239f1-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>

<span data-ttu-id="239f1-120">Bu örnekte, bir sınıfa belirli bir özelliği uygulamak için <xref:System.SerializableAttribute> özniteliği kullanılır:</span><span class="sxs-lookup"><span data-stu-id="239f1-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

```vb
<System.Serializable()> Public Class SampleClass
    ' Objects of this type can be serialized.
End Class
```

 <span data-ttu-id="239f1-121"><xref:System.Runtime.InteropServices.DllImportAttribute> özniteliğine sahip bir yöntem şöyle bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="239f1-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
<System.Runtime.InteropServices.DllImport("user32.dll")>
Sub SampleMethod()
End Sub
```

<span data-ttu-id="239f1-122">Bir bildirime birden fazla öznitelik yerleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="239f1-122">More than one attribute can be placed on a declaration:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
Sub MethodA(<[In](), Out()> ByVal x As Double)
End Sub
Sub MethodB(<Out(), [In]()> ByVal x As Double)
End Sub
```

<span data-ttu-id="239f1-123">Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="239f1-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="239f1-124">Bu tür bir çok kullanım özniteliğine örnek <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="239f1-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

```vb
<Conditional("DEBUG"), Conditional("TEST1")>
Sub TraceMethod()
End Sub
```

> [!NOTE]
> <span data-ttu-id="239f1-125">Kurala göre, tüm öznitelik adları, .NET Framework diğer öğelerden ayırt edilebilmesi için "Attribute" kelimesiyle biter.</span><span class="sxs-lookup"><span data-stu-id="239f1-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="239f1-126">Ancak, koddaki öznitelikleri kullanırken öznitelik sonekini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="239f1-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="239f1-127">Örneğin, `[DllImport]` `[DllImportAttribute]`eşdeğerdir, ancak `DllImportAttribute` özniteliğin gerçek adı .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="239f1-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="239f1-128">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="239f1-128">Attribute Parameters</span></span>

<span data-ttu-id="239f1-129">Birçok özniteliğin, konumsal, adlandırılmamış veya adlandırılmış olabilecek parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="239f1-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="239f1-130">Herhangi bir Konumsal parametre belirli bir sırada belirtilmelidir ve atlanamaz; Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="239f1-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="239f1-131">Konumsal parametreler önce belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="239f1-131">Positional parameters are specified first.</span></span> <span data-ttu-id="239f1-132">Örneğin, bu üç öznitelik eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="239f1-132">For example, these three attributes are equivalent:</span></span>

```vb
<DllImport("user32.dll")>
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>
```

<span data-ttu-id="239f1-133">İlk parametre olan DLL adı, konumsal ve her zaman ilk olarak gelir; diğerleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="239f1-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="239f1-134">Bu durumda, her ikisi de varsayılan olarak false değerine sahiptir, bu nedenle bu parametreler atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="239f1-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="239f1-135">Varsayılan parametre değerleri hakkında bilgi için bağımsız özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="239f1-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="239f1-136">Öznitelik Hedefleri</span><span class="sxs-lookup"><span data-stu-id="239f1-136">Attribute Targets</span></span>

<span data-ttu-id="239f1-137">Bir özniteliğin *hedefi* , özniteliğin uygulandığı varlıktır.</span><span class="sxs-lookup"><span data-stu-id="239f1-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="239f1-138">Örneğin, bir öznitelik bir sınıfa, belirli bir yönteme veya bir derlemenin tamamına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="239f1-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="239f1-139">Varsayılan olarak, bir öznitelik, kendisinden önce gelen öğe için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="239f1-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="239f1-140">Ancak, bir özniteliğin bir yönteme mi, yoksa parametresine mi, yoksa dönüş değerine mi uygulanacağını de açıkça belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="239f1-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="239f1-141">Bir öznitelik hedefini açıkça tanımlamak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="239f1-141">To explicitly identify an attribute target, use the following syntax:</span></span>

```vb
<target : attribute-list>
```

<span data-ttu-id="239f1-142">Olası `target` değerleri listesi aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="239f1-142">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="239f1-143">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="239f1-143">Target value</span></span>|<span data-ttu-id="239f1-144">Uygulama hedefi</span><span class="sxs-lookup"><span data-stu-id="239f1-144">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="239f1-145">Tüm derleme</span><span class="sxs-lookup"><span data-stu-id="239f1-145">Entire assembly</span></span>|
|`module`|<span data-ttu-id="239f1-146">Geçerli derleme modülü (bir Visual Basic modülünden farklı)</span><span class="sxs-lookup"><span data-stu-id="239f1-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|

 <span data-ttu-id="239f1-147">Aşağıdaki örnek, derlemeler ve modüllere özniteliklerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="239f1-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="239f1-148">Daha fazla bilgi için bkz. [ortak öznitelikler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="239f1-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>

```vb
Imports System.Reflection
<Assembly: AssemblyTitleAttribute("Production assembly 4"),
Module: CLSCompliant(True)>
```

## <a name="common-uses-for-attributes"></a><span data-ttu-id="239f1-149">Öznitelikler için ortak kullanımlar</span><span class="sxs-lookup"><span data-stu-id="239f1-149">Common Uses for Attributes</span></span>

<span data-ttu-id="239f1-150">Aşağıdaki listede, kod içindeki özniteliklerin yaygın kullanımları yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="239f1-150">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="239f1-151">Metodun SOAP protokolü üzerinden çağrılabilir olması gerektiğini göstermek için Web hizmetlerindeki `WebMethod` özniteliğini kullanarak yöntemleri işaretleme.</span><span class="sxs-lookup"><span data-stu-id="239f1-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="239f1-152">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="239f1-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>

- <span data-ttu-id="239f1-153">Yerel kodla birlikte çalışırken yöntem parametrelerinin nasıl hazırlanacağını açıklama.</span><span class="sxs-lookup"><span data-stu-id="239f1-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="239f1-154">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="239f1-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

- <span data-ttu-id="239f1-155">Sınıflar, Yöntemler ve arabirimler için COM özelliklerini açıklama.</span><span class="sxs-lookup"><span data-stu-id="239f1-155">Describing the COM properties for classes, methods, and interfaces.</span></span>

- <span data-ttu-id="239f1-156">Yönetilmeyen kod <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfını kullanarak çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="239f1-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>

- <span data-ttu-id="239f1-157">Derlemenizi başlık, sürüm, açıklama veya ticari marka açısından açıklama.</span><span class="sxs-lookup"><span data-stu-id="239f1-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>

- <span data-ttu-id="239f1-158">Bir sınıfın kalıcılığı için hangi üyelerin serileştirmek gerektiğini açıklama.</span><span class="sxs-lookup"><span data-stu-id="239f1-158">Describing which members of a class to serialize for persistence.</span></span>

- <span data-ttu-id="239f1-159">XML ile serileştirme için sınıf üyeleri ve XML düğümleri arasında nasıl eşleme yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="239f1-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>

- <span data-ttu-id="239f1-160">Yöntemler için güvenlik gereksinimlerini açıklama.</span><span class="sxs-lookup"><span data-stu-id="239f1-160">Describing the security requirements for methods.</span></span>

- <span data-ttu-id="239f1-161">Güvenliği zorlamak için kullanılan özellikleri belirtme.</span><span class="sxs-lookup"><span data-stu-id="239f1-161">Specifying characteristics used to enforce security.</span></span>

- <span data-ttu-id="239f1-162">Tam zamanında (JıT) derleyicisine yönelik iyileştirmeler denetleniyor, böylece kod hata ayıklama için kolay kalır.</span><span class="sxs-lookup"><span data-stu-id="239f1-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>

- <span data-ttu-id="239f1-163">Bir yönteme arayan hakkında bilgi alma.</span><span class="sxs-lookup"><span data-stu-id="239f1-163">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="239f1-164">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="239f1-164">Related Sections</span></span>

<span data-ttu-id="239f1-165">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="239f1-165">For more information, see:</span></span>

- [<span data-ttu-id="239f1-166">Özel öznitelikler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="239f1-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)

- [<span data-ttu-id="239f1-167">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="239f1-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

- [<span data-ttu-id="239f1-168">Nasıl yapılır: öznitelikleri kullanarak C/C++ Union oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="239f1-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)

- [<span data-ttu-id="239f1-169">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="239f1-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)

- [<span data-ttu-id="239f1-170">Arayan bilgileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="239f1-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)

## <a name="see-also"></a><span data-ttu-id="239f1-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="239f1-171">See also</span></span>

- [<span data-ttu-id="239f1-172">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="239f1-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="239f1-173">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="239f1-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="239f1-174">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="239f1-174">Attributes</span></span>](../../../../standard/attributes/index.md)
