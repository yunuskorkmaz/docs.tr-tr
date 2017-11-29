---
title: "Öznitelikler (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2993ef3f424aa6487681e194f21e0f82193342ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-c"></a><span data-ttu-id="3017c-102">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="3017c-102">Attributes (C#)</span></span>
<span data-ttu-id="3017c-103">Öznitelikler meta verileri veya tanımlayıcı bilgileri (derleme, türleri, yöntemler, özellikler ve benzeri) kodu ile ilişkilendirme için güçlü bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="3017c-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="3017c-104">Öznitelik bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında adlı bir yöntemi kullanarak sorgulanabilir *yansıma*.</span><span class="sxs-lookup"><span data-stu-id="3017c-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="3017c-105">Daha fazla bilgi için bkz: [yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="3017c-105">For more information, see [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="3017c-106">Öznitelikler, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3017c-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="3017c-107">Öznitelikleri programınıza meta veri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3017c-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="3017c-108">*Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="3017c-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="3017c-109">Tüm .NET derlemelerini belirlenen türleri ve derlemede tanımlanan tür üyeleri açıklayan meta veriler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3017c-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="3017c-110">Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3017c-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="3017c-111">Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3017c-111">For more information, see, [Creating Custom Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="3017c-112">Tüm derlemeler, modüller veya daha küçük program öğeleri sınıfları ve özellikleri gibi bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3017c-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="3017c-113">Öznitelikler, yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="3017c-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="3017c-114">Programınızı kendi meta verileri veya diğer programları meta yansıma kullanarak inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3017c-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="3017c-115">Daha fazla bilgi için bkz: [yansıma (C#) kullanarak erişme özniteliklerle](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="3017c-115">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="3017c-116">Öznitelikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="3017c-116">Using Attributes</span></span>  
 <span data-ttu-id="3017c-117">Belirli bir özniteliği, geçerli olduğu bildirimleri türlerini kısıtlayacak ancak öznitelikleri pek çok bildiriminde, yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3017c-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="3017c-118">C# ' ta, bir öznitelik köşeli parantez ([]) içine özniteliğinin adı girerek geçerli olduğu varlık bildiriminin üstüne belirtin.</span><span class="sxs-lookup"><span data-stu-id="3017c-118">In C#, you specify an attribute by placing the name of the attribute, enclosed in square brackets ([]), above the declaration of the entity to which it applies.</span></span>  
  
 <span data-ttu-id="3017c-119">Bu örnekte, <xref:System.SerializableAttribute> özniteliği bir sınıf için belirli bir karakteristik uygulamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="3017c-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 <span data-ttu-id="3017c-120">Öznitelik bir yöntemle <xref:System.Runtime.InteropServices.DllImportAttribute> şöyle bildirilmiş:</span><span class="sxs-lookup"><span data-stu-id="3017c-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 <span data-ttu-id="3017c-121">Birden fazla öznitelik bir bildiriminde yerleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="3017c-121">More than one attribute can be placed on a declaration:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 <span data-ttu-id="3017c-122">Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="3017c-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="3017c-123">Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="3017c-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="3017c-124">Kurala göre .NET Framework'teki diğer öğelerini bunları ayırt etmek için "özniteliği" word tüm öznitelik adları bitemez.</span><span class="sxs-lookup"><span data-stu-id="3017c-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="3017c-125">Ancak, öznitelikler kodda kullanırken özniteliği soneki belirtmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3017c-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="3017c-126">Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework'teki özniteliğin gerçek adıdır.</span><span class="sxs-lookup"><span data-stu-id="3017c-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="3017c-127">Öznitelik parametreleri</span><span class="sxs-lookup"><span data-stu-id="3017c-127">Attribute Parameters</span></span>  
 <span data-ttu-id="3017c-128">Konumsal, adlandırılmamış veya adlandırılmış parametreleri birçok özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3017c-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="3017c-129">Konumsal parametreleri belirli bir sırada belirtilmeli ve atlanmış olamaz; adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="3017c-129">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="3017c-130">Konumsal parametreler ilk belirtildi.</span><span class="sxs-lookup"><span data-stu-id="3017c-130">Positional parameters are specified first.</span></span> <span data-ttu-id="3017c-131">Örneğin, bu üç özniteliğin eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="3017c-131">For example, these three attributes are equivalent:</span></span>  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 <span data-ttu-id="3017c-132">İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğer olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3017c-132">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="3017c-133">Bu durumda, kullanıcılar atlanabilir şekilde her ikisi de false, parametreleri varsayılan adı.</span><span class="sxs-lookup"><span data-stu-id="3017c-133">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="3017c-134">Varsayılan parametre değerleri hakkında bilgi için tek tek özniteliğin belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="3017c-134">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="3017c-135">Öznitelik Hedefleri</span><span class="sxs-lookup"><span data-stu-id="3017c-135">Attribute Targets</span></span>  
 <span data-ttu-id="3017c-136">*Hedef* bir öznitelik geçerli olduğu varlık özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="3017c-136">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="3017c-137">Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme için geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="3017c-137">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="3017c-138">Varsayılan olarak, bir öznitelik yakalanması öğesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3017c-138">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="3017c-139">Ancak bir öznitelik bir yöntem veya onun parametresi veya dönüş değeri uygulanıp uygulanmayacağını, aynı zamanda açıkça, örneğin, tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3017c-139">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="3017c-140">Açıkça bir öznitelik hedefini belirlemek için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="3017c-140">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```csharp  
[target : attribute-list]  
```  
  
 <span data-ttu-id="3017c-141">Olası listesi `target` değerleri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3017c-141">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="3017c-142">Hedef değer</span><span class="sxs-lookup"><span data-stu-id="3017c-142">Target value</span></span>|<span data-ttu-id="3017c-143">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="3017c-143">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="3017c-144">Tüm derleme</span><span class="sxs-lookup"><span data-stu-id="3017c-144">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="3017c-145">Geçerli derleme Modülü</span><span class="sxs-lookup"><span data-stu-id="3017c-145">Current assembly module</span></span>|  
|`field`|<span data-ttu-id="3017c-146">Bir sınıf veya yapı alanında</span><span class="sxs-lookup"><span data-stu-id="3017c-146">Field in a class or a struct</span></span>|  
|`event`|<span data-ttu-id="3017c-147">Olay</span><span class="sxs-lookup"><span data-stu-id="3017c-147">Event</span></span>|  
|`method`|<span data-ttu-id="3017c-148">Yöntem veya `get` ve `set` özellik erişimcisi</span><span class="sxs-lookup"><span data-stu-id="3017c-148">Method or `get` and `set` property accessors</span></span>|  
|`param`|<span data-ttu-id="3017c-149">Yöntem parametreleri veya `set` özellik erişimcisi parametreleri</span><span class="sxs-lookup"><span data-stu-id="3017c-149">Method parameters or `set` property accessor parameters</span></span>|  
|`property`|<span data-ttu-id="3017c-150">Özellik</span><span class="sxs-lookup"><span data-stu-id="3017c-150">Property</span></span>|  
|`return`|<span data-ttu-id="3017c-151">Yöntemi, özelliği dizin oluşturucu, değeri döndürür veya `get` özelliği erişimcisi</span><span class="sxs-lookup"><span data-stu-id="3017c-151">Return value of a method, property indexer, or `get` property accessor</span></span>|  
|`type`|<span data-ttu-id="3017c-152">Yapısı, sınıf, arabirim, numaralandırma veya temsilci</span><span class="sxs-lookup"><span data-stu-id="3017c-152">Struct, class, interface, enum, or delegate</span></span>|  
  
 <span data-ttu-id="3017c-153">Aşağıdaki örnek, derlemeler ve modüller öznitelikleri uygulanacak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3017c-153">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="3017c-154">Daha fazla bilgi için bkz: [ortak öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3017c-154">For more information, see [Common Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 <span data-ttu-id="3017c-155">Aşağıdaki örnekte, yöntem, yöntem parametreleri, öznitelikleri uygulamak gösterilmiştir ve yöntemi dönüş değerleri C# '.</span><span class="sxs-lookup"><span data-stu-id="3017c-155">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  <span data-ttu-id="3017c-156">Hedefler, bağımsız olarak `SomeAttr` geçerli olması için tanımlanan `return` hedef sahip belirtilmesi bile `SomeAttr` yalnızca dönüş değerleri uygulamak için tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="3017c-156">Regardless of the targets on which `SomeAttr` is defined to be valid, the `return` target has to be specified, even if `SomeAttr` were defined to apply only to return values.</span></span> <span data-ttu-id="3017c-157">Diğer bir deyişle, derleyici kullanmaz `AttributeUsage` bilgileri belirsiz öznitelik hedefleri çözümlemek için.</span><span class="sxs-lookup"><span data-stu-id="3017c-157">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="3017c-158">Daha fazla bilgi için bkz: [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="3017c-158">For more information, see [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span></span>  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="3017c-159">Öznitelikler için ortak kullanımlar</span><span class="sxs-lookup"><span data-stu-id="3017c-159">Common Uses for Attributes</span></span>  
 <span data-ttu-id="3017c-160">Aşağıdaki öznitelikler'ın yaygın kullanımları bazılarını kod içerir:</span><span class="sxs-lookup"><span data-stu-id="3017c-160">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="3017c-161">Yöntemlerini kullanarak işaretleme `WebMethod` yöntemi SOAP protokolü üzerinden aranabilir olması gerektiğini belirtmek için Web Hizmetleri içinde öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3017c-161">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="3017c-162">Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3017c-162">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="3017c-163">Yerel kod ile birlikte çalışırken yöntem parametreleri sıralamakta nasıl açıklayan.</span><span class="sxs-lookup"><span data-stu-id="3017c-163">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="3017c-164">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3017c-164">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="3017c-165">Sınıfları, yöntemleri ve arabirimleri COM özelliklerini açıklayan.</span><span class="sxs-lookup"><span data-stu-id="3017c-165">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="3017c-166">Yönetilmeyen çağırma kullanarak kod <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3017c-166">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="3017c-167">Başlık, sürüm, açıklama veya ticari marka bakımından derlemenizi açıklayan.</span><span class="sxs-lookup"><span data-stu-id="3017c-167">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="3017c-168">Kalıcılığını serileştirmek için bir sınıf hangi üyelerinin açıklayan.</span><span class="sxs-lookup"><span data-stu-id="3017c-168">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="3017c-169">Sınıf üyeleri ve XML serileştirme için XML düğümler arasında eşleme açıklayan.</span><span class="sxs-lookup"><span data-stu-id="3017c-169">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="3017c-170">Yöntemleri için güvenlik gereksinimleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3017c-170">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="3017c-171">Güvenlik uygulamak için kullanılan özellikleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="3017c-171">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="3017c-172">Böylece kodu hata ayıklamak kolay tam zamanında (JIT) derleyici tarafından iyileştirmeleri denetleme.</span><span class="sxs-lookup"><span data-stu-id="3017c-172">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="3017c-173">Arayan bir yöntemi hakkında bilgi edinme.</span><span class="sxs-lookup"><span data-stu-id="3017c-173">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3017c-174">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3017c-174">Related Sections</span></span>  
 <span data-ttu-id="3017c-175">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="3017c-175">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3017c-176">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="3017c-176">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="3017c-177">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="3017c-177">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="3017c-178">Nasıl yapılır: öznitelikleri (C#) kullanarak C/C++ birleşimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3017c-178">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="3017c-179">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="3017c-179">Common Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="3017c-180">Arayan bilgileri (C#)</span><span class="sxs-lookup"><span data-stu-id="3017c-180">Caller Information (C#)</span></span>](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="3017c-181">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3017c-181">See Also</span></span>  
 [<span data-ttu-id="3017c-182">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3017c-182">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3017c-183">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="3017c-183">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="3017c-184">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3017c-184">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)
