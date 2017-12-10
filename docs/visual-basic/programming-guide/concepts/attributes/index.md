---
title: "Öznitelikler genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: efdfa297099fb5538e7b92514c8440c2722f3fe1
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="b7cdc-102">Öznitelikler genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7cdc-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="b7cdc-103">Öznitelikler meta verileri veya tanımlayıcı bilgileri (derleme, türleri, yöntemler, özellikler ve benzeri) kodu ile ilişkilendirme için güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="b7cdc-104">Öznitelik bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında adlı bir yöntemi kullanarak sorgulanabilir *yansıma*.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="b7cdc-105">Daha fazla bilgi için bkz: [yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="b7cdc-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="b7cdc-106">Öznitelikler, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="b7cdc-107">Öznitelikleri programınıza meta veri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="b7cdc-108">*Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="b7cdc-109">Tüm .NET derlemelerini belirlenen türleri ve derlemede tanımlanan tür üyeleri açıklayan meta veriler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="b7cdc-110">Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="b7cdc-111">Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b7cdc-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="b7cdc-112">Tüm derlemeler, modüller veya daha küçük program öğeleri sınıfları ve özellikleri gibi bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="b7cdc-113">Öznitelikler, yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="b7cdc-114">Programınızı kendi meta verileri veya diğer programları meta yansıma kullanarak inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="b7cdc-115">Daha fazla bilgi için bkz: [erişme öznitelikleri kullanarak yansıma (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="b7cdc-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="b7cdc-116">Öznitelikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="b7cdc-116">Using Attributes</span></span>  
 <span data-ttu-id="b7cdc-117">Belirli bir özniteliği, geçerli olduğu bildirimleri türlerini kısıtlayacak ancak öznitelikleri pek çok bildiriminde, yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="b7cdc-118">Visual Basic'te bir öznitelik açılı ayraç (\< >).</span><span class="sxs-lookup"><span data-stu-id="b7cdc-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="b7cdc-119">Bu, aynı satırda uygulandığı öğe hemen önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="b7cdc-120">Bu örnekte, <xref:System.SerializableAttribute> özniteliği bir sınıf için belirli bir karakteristik uygulamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="b7cdc-121">Öznitelik bir yöntemle <xref:System.Runtime.InteropServices.DllImportAttribute> şöyle bildirilmiş:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="b7cdc-122">Birden fazla öznitelik bir bildiriminde yerleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="b7cdc-123">Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="b7cdc-124">Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="b7cdc-125">Kurala göre .NET Framework'teki diğer öğelerini bunları ayırt etmek için "özniteliği" word tüm öznitelik adları bitemez.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="b7cdc-126">Ancak, öznitelikler kodda kullanırken özniteliği soneki belirtmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="b7cdc-127">Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework'teki özniteliğin gerçek adıdır.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="b7cdc-128">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="b7cdc-128">Attribute Parameters</span></span>  
 <span data-ttu-id="b7cdc-129">Konumsal, adlandırılmamış veya adlandırılmış parametreleri birçok özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="b7cdc-130">Konumsal parametreleri belirli bir sırada belirtilmeli ve atlanmış olamaz; adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="b7cdc-131">Konumsal parametreler ilk belirtildi.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-131">Positional parameters are specified first.</span></span> <span data-ttu-id="b7cdc-132">Örneğin, bu üç özniteliğin eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="b7cdc-133">İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğer olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="b7cdc-134">Bu durumda, kullanıcılar atlanabilir şekilde her ikisi de false, parametreleri varsayılan adı.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="b7cdc-135">Varsayılan parametre değerleri hakkında bilgi için tek tek özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="b7cdc-136">Öznitelik Hedefleri</span><span class="sxs-lookup"><span data-stu-id="b7cdc-136">Attribute Targets</span></span>  
 <span data-ttu-id="b7cdc-137">*Hedef* bir öznitelik geçerli olduğu varlık özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="b7cdc-138">Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme için geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="b7cdc-139">Varsayılan olarak, bir öznitelik yakalanması öğesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="b7cdc-140">Ancak bir öznitelik bir yöntem veya onun parametresi veya dönüş değeri uygulanıp uygulanmayacağını, aynı zamanda açıkça, örneğin, tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="b7cdc-141">Açıkça bir öznitelik hedefini belirlemek için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="b7cdc-142">Olası listesi `target` değerleri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="b7cdc-143">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="b7cdc-143">Target value</span></span>|<span data-ttu-id="b7cdc-144">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="b7cdc-145">Tüm derleme</span><span class="sxs-lookup"><span data-stu-id="b7cdc-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="b7cdc-146">(Visual Basic modülünden farklı) geçerli derleme Modülü</span><span class="sxs-lookup"><span data-stu-id="b7cdc-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="b7cdc-147">Aşağıdaki örnek, derlemeler ve modüller öznitelikleri uygulanacak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="b7cdc-148">Daha fazla bilgi için bkz: [ortak öznitelikler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b7cdc-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="b7cdc-149">Öznitelikler için ortak kullanımlar</span><span class="sxs-lookup"><span data-stu-id="b7cdc-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="b7cdc-150">Aşağıdaki öznitelikler'ın yaygın kullanımları bazılarını kod içerir:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="b7cdc-151">Yöntemlerini kullanarak işaretleme `WebMethod` yöntemi SOAP protokolü üzerinden aranabilir olması gerektiğini belirtmek için Web Hizmetleri içinde öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="b7cdc-152">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="b7cdc-153">Yerel kod ile birlikte çalışırken yöntem parametreleri sıralamakta nasıl açıklayan.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="b7cdc-154">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="b7cdc-155">Sınıfları, yöntemleri ve arabirimleri COM özelliklerini açıklayan.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="b7cdc-156">Yönetilmeyen çağırma kullanarak kod <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="b7cdc-157">Başlık, sürüm, açıklama veya ticari marka bakımından derlemenizi açıklayan.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="b7cdc-158">Kalıcılığını serileştirmek için bir sınıf hangi üyelerinin açıklayan.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-158">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="b7cdc-159">Sınıf üyeleri ve XML serileştirme için XML düğümler arasında eşleme açıklayan.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="b7cdc-160">Yöntemleri için güvenlik gereksinimleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-160">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="b7cdc-161">Güvenlik uygulamak için kullanılan özellikleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-161">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="b7cdc-162">Böylece kodu hata ayıklamak kolay tam zamanında (JIT) derleyici tarafından iyileştirmeleri denetleme.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="b7cdc-163">Arayan bir yöntemi hakkında bilgi edinme.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b7cdc-164">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b7cdc-164">Related Sections</span></span>  
 <span data-ttu-id="b7cdc-165">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="b7cdc-165">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b7cdc-166">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="b7cdc-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="b7cdc-167">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="b7cdc-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="b7cdc-168">Nasıl yapılır: öznitelikleri (Visual Basic) kullanarak C/C++ birleşimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b7cdc-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="b7cdc-169">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7cdc-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="b7cdc-170">Arayan bilgileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7cdc-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7cdc-171">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7cdc-171">See Also</span></span>  
 [<span data-ttu-id="b7cdc-172">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b7cdc-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="b7cdc-173">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7cdc-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="b7cdc-174">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b7cdc-174">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)
