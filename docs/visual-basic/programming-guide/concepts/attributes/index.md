---
title: Öznitelikler genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: bb012b49c76963306d723d7732b4c7054bf13ebb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827698"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="dc752-102">Öznitelikler genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc752-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="dc752-103">Öznitelikler (derlemeler, türler, yöntemler, özellikler ve benzeri) koduyla ilişkili bir meta veriler ya da tanımlayıcı bilgileri, güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc752-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="dc752-104">Öznitelik, bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında olarak adlandırılan tekniği kullanarak sorgulanabilir *yansıma*.</span><span class="sxs-lookup"><span data-stu-id="dc752-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="dc752-105">Daha fazla bilgi için [yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="dc752-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="dc752-106">Öznitelik, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="dc752-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="dc752-107">Öznitelik meta verileri programınıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dc752-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="dc752-108">*Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="dc752-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="dc752-109">Tüm .NET derlemeleri derlemede tanımlanan tür üyeleri ve türleri açıklayan meta veriler belirtilen bir kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="dc752-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="dc752-110">Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc752-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="dc752-111">Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="dc752-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="dc752-112">Tüm derlemeler, modüller veya daha küçük program öğelerini sınıfları ve özellikleri gibi bir veya daha fazla öznitelikleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc752-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="dc752-113">Öznitelikleri yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="dc752-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="dc752-114">Programınızı kendi meta veriler ya da diğer programları meta verilerde yansıma kullanarak inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc752-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="dc752-115">Daha fazla bilgi için [erişme öznitelikleri kullanarak yansıma (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="dc752-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="dc752-116">Öznitelikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="dc752-116">Using Attributes</span></span>  
 <span data-ttu-id="dc752-117">Belirli bir öznitelik bildirimleri, geçerli olduğu türlerini kısıtlamak ancak öznitelikleri pek çok bildiriminde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="dc752-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="dc752-118">Visual Basic'te, bir öznitelik açılı ayraç içine alınır (\< >).</span><span class="sxs-lookup"><span data-stu-id="dc752-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="dc752-119">Bu, aynı satırda uygulandığı öğenin hemen önce yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc752-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="dc752-120">Bu örnekte, <xref:System.SerializableAttribute> özniteliği, belirli bir özellik için bir sınıf uygulamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="dc752-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="dc752-121">Özniteliğine sahip metot <xref:System.Runtime.InteropServices.DllImportAttribute> şu şekilde bildirilir:</span><span class="sxs-lookup"><span data-stu-id="dc752-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="dc752-122">Birden fazla özniteliği bir bildiriminde yerleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="dc752-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="dc752-123">Bazı öznitelikleri kereden fazla belirli bir varlık için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="dc752-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="dc752-124">Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="dc752-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="dc752-125">Kural gereği, tüm öznitelik adları word .NET Framework'teki diğer öğelerden bunları ayırt etmek için "özniteliği" ile biter.</span><span class="sxs-lookup"><span data-stu-id="dc752-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="dc752-126">Ancak, öznitelikler kodda kullanıldığında özniteliği soneki belirtmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dc752-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="dc752-127">Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework'teki özniteliğin gerçek adıdır.</span><span class="sxs-lookup"><span data-stu-id="dc752-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="dc752-128">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="dc752-128">Attribute Parameters</span></span>  
 <span data-ttu-id="dc752-129">Konumsal, adlandırılmamış veya adlandırılmış parametreleri fazla öznitelik var.</span><span class="sxs-lookup"><span data-stu-id="dc752-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="dc752-130">Konumsal parametreleri belirli bir sırayla belirtilmelidir ve atlanamaz. adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="dc752-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="dc752-131">Konumsal parametreler ilk belirtilir.</span><span class="sxs-lookup"><span data-stu-id="dc752-131">Positional parameters are specified first.</span></span> <span data-ttu-id="dc752-132">Örneğin, bu üç özniteliğin eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="dc752-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="dc752-133">İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğerleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="dc752-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="dc752-134">Bu durumda, döngülerinden çıkarılabilir şekilde her ikisi de false olarak parametreleri varsayılan adı.</span><span class="sxs-lookup"><span data-stu-id="dc752-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="dc752-135">Varsayılan parametre değerleri hakkında bilgi için tek bir özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="dc752-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="dc752-136">Öznitelik Hedefleri</span><span class="sxs-lookup"><span data-stu-id="dc752-136">Attribute Targets</span></span>  
 <span data-ttu-id="dc752-137">*Hedef* özniteliği öznitelik uygulandığı varlıktır.</span><span class="sxs-lookup"><span data-stu-id="dc752-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="dc752-138">Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc752-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="dc752-139">Varsayılan olarak, kendisinden öğe için bir özniteliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="dc752-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="dc752-140">Ancak, bir yöntem veya, parametre veya dönüş değeri bir öznitelik uygulanmış olup olmadığını açıkça, örneğin, belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc752-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="dc752-141">Bir öznitelik hedefi açıkça tanımlamak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="dc752-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="dc752-142">Olası listesini `target` değerleri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dc752-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="dc752-143">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="dc752-143">Target value</span></span>|<span data-ttu-id="dc752-144">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="dc752-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="dc752-145">Tüm derleme</span><span class="sxs-lookup"><span data-stu-id="dc752-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="dc752-146">(Visual Basic modülünden farklıdır) geçerli derleme Modülü</span><span class="sxs-lookup"><span data-stu-id="dc752-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="dc752-147">Aşağıdaki örnek, derlemeler ve modüller için öznitelik uygulayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc752-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="dc752-148">Daha fazla bilgi için [ortak öznitelikler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="dc752-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="dc752-149">Öznitelikler için yaygın kullanımları</span><span class="sxs-lookup"><span data-stu-id="dc752-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="dc752-150">Aşağıdaki liste, kod öznitelikleri'nın yaygın kullanımları birkaçını içerir:</span><span class="sxs-lookup"><span data-stu-id="dc752-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="dc752-151">Yöntemlerini kullanarak işaretleme `WebMethod` Web Hizmetleri yöntemi SOAP protokolü üzerinden çağrılabilmelidir belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc752-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="dc752-152">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dc752-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="dc752-153">Yerel kod ile birlikte çalışırken yöntem parametreleri'ı sıralama nasıl açıklayan.</span><span class="sxs-lookup"><span data-stu-id="dc752-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="dc752-154">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dc752-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="dc752-155">Sınıfları, yöntemleri ve arabirimleri için COM özelliklerini açıklayan.</span><span class="sxs-lookup"><span data-stu-id="dc752-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="dc752-156">Yönetilmeyen çağırma kod kullanarak <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dc752-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="dc752-157">Başlık, sürüm, açıklama veya ticari marka açısından derlemenizi açıklayan.</span><span class="sxs-lookup"><span data-stu-id="dc752-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="dc752-158">Kalıcılık için seri hale getirmek için bir sınıfın hangi üyelerinin açıklayan.</span><span class="sxs-lookup"><span data-stu-id="dc752-158">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="dc752-159">Sınıf üyeleri için XML serileştirme XML düğümler arasındaki eşlemeyle ilgili bilgi açıklayan.</span><span class="sxs-lookup"><span data-stu-id="dc752-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="dc752-160">Güvenlik gereksinimleri yöntemleri için açıklama.</span><span class="sxs-lookup"><span data-stu-id="dc752-160">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="dc752-161">Güvenliği zorlamak için kullanılan özellikleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="dc752-161">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="dc752-162">Kod hatalarını ayıklamak kolay kalır. böylece en iyi duruma getirme just-in-time (JIT) derleyici tarafından denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="dc752-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="dc752-163">Bir yöntemin arayanı hakkında bilgi edinme.</span><span class="sxs-lookup"><span data-stu-id="dc752-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dc752-164">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dc752-164">Related Sections</span></span>  
 <span data-ttu-id="dc752-165">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="dc752-165">For more information, see:</span></span>  
  
-   [<span data-ttu-id="dc752-166">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc752-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="dc752-167">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="dc752-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="dc752-168">Nasıl yapılır: Öznitelikler (Visual Basic) kullanarak bir C/C++ birleşimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc752-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="dc752-169">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc752-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="dc752-170">Arayan bilgileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc752-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="dc752-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc752-171">See also</span></span>

- [<span data-ttu-id="dc752-172">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dc752-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="dc752-173">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc752-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="dc752-174">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dc752-174">Attributes</span></span>](../../../../standard/attributes/index.md)
