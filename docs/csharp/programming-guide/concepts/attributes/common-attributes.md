---
title: "Ortak öznitelikler (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aded9c9b2e8c253eebd6c71782f0bff6ca0104ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="common-attributes-c"></a><span data-ttu-id="b3bcc-102">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="b3bcc-102">Common Attributes (C#)</span></span>
<span data-ttu-id="b3bcc-103">Bu konuda, C# programlarında en yaygın olarak kullanılan öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
-   [<span data-ttu-id="b3bcc-104">Genel Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b3bcc-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="b3bcc-105">Artık kullanılmayan özniteliği</span><span class="sxs-lookup"><span data-stu-id="b3bcc-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="b3bcc-106">Koşul özniteliği</span><span class="sxs-lookup"><span data-stu-id="b3bcc-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="b3bcc-107">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
##  <span data-ttu-id="b3bcc-108"><a name="Global"></a>Genel Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b3bcc-108"><a name="Global"></a> Global Attributes</span></span>  
 <span data-ttu-id="b3bcc-109">Çoğu öznitelik sınıfları veya yöntemleri gibi belirli bir dil öğeleri uygulanır; Ancak, bazı öznitelikler genel — tüm derleme veya modülü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="b3bcc-110">Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği, böyle bir bütünleştirilmiş sürüm bilgilerini eklemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="b3bcc-111">Genel Öznitelikler görünen kaynak kodunda herhangi sonra en üst düzey `using` yönergeleri ve herhangi bir tür, modül veya ad alanı bildirimleri öncesinde.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="b3bcc-112">Genel Öznitelikler birden çok kaynak dosyalarında görünebilir, ancak dosyaları tek bir derleme geçişinde derlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="b3bcc-113">C# projelerinde, genel öznitelikler AssemblyInfo.cs dosyasında yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="b3bcc-114">Derleme özniteliklerinin bir derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="b3bcc-115">Bunlar aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-115">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="b3bcc-116">Derleme kimlik öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-116">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="b3bcc-117">Bilgilendirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-117">Informational attributes</span></span>  
  
-   <span data-ttu-id="b3bcc-118">Derleme bildirimi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="b3bcc-119">Derleme kimlik öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="b3bcc-120">Üç özniteliklerle (tanımlayıcı ad, eğer varsa) bir derleme kimliğini belirlemek: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="b3bcc-121">Bu öznitelikler derlemenin tam adını formunu ve kodda başvurduğunuzda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="b3bcc-122">Bir derlemenin sürüm ve öznitelikleri kullanarak kültür ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="b3bcc-123">Ancak, ad değeri Visual Studio IDE içinde derleyici tarafından ayarlanır [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box), ya da derleme bağlayıcı (derleme oluşturulduğunda Al.exe) derleme bildirimi içeren dosyayı alarak.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="b3bcc-124"><xref:System.Reflection.AssemblyFlagsAttribute> Özniteliği, derleme birden çok kopyasını bir arada var olabilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="b3bcc-125">Aşağıdaki tabloda kimlik öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="b3bcc-126">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b3bcc-126">Attribute</span></span>|<span data-ttu-id="b3bcc-127">Amaç</span><span class="sxs-lookup"><span data-stu-id="b3bcc-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="b3bcc-128">Tam olarak bir derleme kimliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="b3bcc-129">Bir derlemeyi sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="b3bcc-130">Hangi derleme destekler kültür belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="b3bcc-131">Bir derlemeyi aynı bilgisayardaki aynı işlemde ya da aynı uygulama etki alanında yan yana yürütme destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="b3bcc-132">Bilgilendirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-132">Informational Attributes</span></span>  
 <span data-ttu-id="b3bcc-133">Bilgilendirme öznitelikleri, ek şirket veya bir derleme için ürün bilgi sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="b3bcc-134">Aşağıdaki tabloda tanımlanan bilgilendirme öznitelikleri gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="b3bcc-135">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b3bcc-135">Attribute</span></span>|<span data-ttu-id="b3bcc-136">Amaç</span><span class="sxs-lookup"><span data-stu-id="b3bcc-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="b3bcc-137">Derleme bildirimi ürün adını belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="b3bcc-138">Derleme bildirimi için bir ticari marka belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="b3bcc-139">Derleme bildirimi için bilgilendirici bir sürümünü belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="b3bcc-140">Derleme bildirimi için bir şirket adı belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="b3bcc-141">Derleme bildirimi için telif hakkı belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="b3bcc-142">Derleyicinin Win32 dosya sürümü kaynak için belirli bir sürüm numarasını kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="b3bcc-143">Derleme ortak dil belirtimi (CLS) ile uyumlu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="b3bcc-144">Derleme bildirimi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="b3bcc-145">Derleme bildirimi özniteliklerinin derleme bildirimi bilgi sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="b3bcc-146">Bu başlık, açıklama, varsayılan diğer ad ve yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="b3bcc-147">Derleme bildirimi öznitelikleri tanımlanan aşağıdaki tabloda gösterilmektedir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="b3bcc-148">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b3bcc-148">Attribute</span></span>|<span data-ttu-id="b3bcc-149">Amaç</span><span class="sxs-lookup"><span data-stu-id="b3bcc-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="b3bcc-150">Derleme bildirimi için bir derleme başlık belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="b3bcc-151">Derleme bildirimi derleme açıklamasını belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="b3bcc-152">Bir derleme yapılandırmasını (örneğin, tekil veya hata ayıklama) belirten özel bir öznitelik için bir derleme bildirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="b3bcc-153">Derleme bildirimi için bir kolay varsayılan diğer adı tanımlar</span><span class="sxs-lookup"><span data-stu-id="b3bcc-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <span data-ttu-id="b3bcc-154"><a name="Obsolete"></a>Artık kullanılmayan özniteliği</span><span class="sxs-lookup"><span data-stu-id="b3bcc-154"><a name="Obsolete"></a> Obsolete Attribute</span></span>  
 <span data-ttu-id="b3bcc-155">`Obsolete` Özniteliği bir program varlık artık kullanım için önerilen biri olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="b3bcc-156">Artık kullanılmayan olarak işaretlenmiş bir varlığın her kullanın, daha sonra bir uyarı veya öznitelik nasıl yapılandırıldığına bağlı olarak bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="b3bcc-157">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-157">For example:</span></span>  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 <span data-ttu-id="b3bcc-158">Bu örnekte `Obsolete` özniteliği sınıfına uygulanan `A` ve yöntemine `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="b3bcc-159">Öznitelik oluşturucunun ikinci bağımsız değişkeni uygulanan çünkü `B.OldMethod` ayarlanır `true`, bu yöntem, sınıfını kullanarak ancak derleyici hatası neden olur `A` bir uyarı yalnızca ürettiği olur.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="b3bcc-160">Çağırma `B.NewMethod`, ancak hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="b3bcc-161">Öznitelik oluşturucunun ilk bağımsız değişkeni olarak sağlanan dize uyarı veya hata bir parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="b3bcc-162">Örneğin, önceki tanımları ile kullandığınızda, aşağıdaki kod iki uyarılar ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="b3bcc-163">Sınıfı için iki uyarıları `A` oluşturulur: sınıf başvurusu bildirimi için diğeri için sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="b3bcc-164">`Obsolete` Öznitelik bağımsız değişkenler olmadan kullanılabilir, ancak neden bir açıklaması da dahil olmak üzere öğe kullanılmıyor ve ne kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="b3bcc-165">`Obsolete` Özniteliği bir tek kullanımlık özniteliği ve öznitelikleri veren herhangi bir varlık için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="b3bcc-166">`Obsolete`bir diğer adı için <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <span data-ttu-id="b3bcc-167"><a name="Conditional"></a>Koşul özniteliği</span><span class="sxs-lookup"><span data-stu-id="b3bcc-167"><a name="Conditional"></a> Conditional Attribute</span></span>  
 <span data-ttu-id="b3bcc-168">`Conditional` Özniteliği bir yönteminin yürütülmesi üzerinde önişlem tanımlayıcısını bağımlı yapar.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="b3bcc-169">`Conditional` Özniteliktir için diğer ad <xref:System.Diagnostics.ConditionalAttribute>ve bir yöntem veya öznitelik sınıfı için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="b3bcc-170">Bu örnekte, `Conditional` etkinleştirmek veya programa özgü tanı bilgilerini görüntülemeyi devre dışı bırakmak için bir yönteme uygulanır:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 <span data-ttu-id="b3bcc-171">Varsa `TRACE_ON` tanımlayıcısı tanımlı değil, izleme çıktısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="b3bcc-172">`Conditional` Özniteliği ile kullanılan genellikle `DEBUG` izleme ve hata ayıklama derlemeleri ancak içinde değil yayın derlemeler, günlük özellikleri etkinleştirmek için tanımlayıcı şöyle:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="b3bcc-173">Koşullu olarak işaretli bir yöntem çağrıldığında, varlığının veya yokluğunun belirtilen önişlem simgenin çağrı dahil atlanmış verilip verilmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="b3bcc-174">Simgenin tanımlanmışsa, çağrı bulunur; Aksi halde çağrı atlanır.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="b3bcc-175">Kullanarak `Conditional` bir temizleyici olan yöntemleri içinde kapsayan daha zarif ve hataya daha az alternatif `#if…#endif` blokları, şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="b3bcc-176">Koşullu bir yöntem sınıfta veya yapı bildiriminde bir yöntem olmalıdır ve bir dönüş değeri olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="b3bcc-177">Birden çok tanımlayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="b3bcc-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="b3bcc-178">Bir yöntemin birden çok varsa `Conditional` öznitelikleri yöntemine bir çağrı dahil en az bir koşullu simgelerin tanımlanmışsa (diğer bir deyişle, simgeler mantıksal veya işlecini kullanarak birbirine bağlıdır).</span><span class="sxs-lookup"><span data-stu-id="b3bcc-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="b3bcc-179">Bu örnekte, ya da varlığını `A` veya `B` bir yöntem çağrısı neden olur:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="b3bcc-180">Mantıksal ve işlecini kullanarak simgeleri bağlama etkisini elde etmek için seri koşullu yöntemler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="b3bcc-181">Örneğin, aşağıdaki ikinci yöntem yalnızca her iki yürütecek `A` ve `B` tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="b3bcc-182">Koşullu öznitelik sınıfları ile kullanma</span><span class="sxs-lookup"><span data-stu-id="b3bcc-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="b3bcc-183">`Conditional` Özniteliği için öznitelik sınıf tanımını da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="b3bcc-184">Bu örnekte, özel öznitelik `Documentation` hata ayıklama tanımlanmışsa, yalnızca bilgi meta verileri ekler.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
##  <span data-ttu-id="b3bcc-185"><a name="CallerInfo"></a>Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-185"><a name="CallerInfo"></a> Caller Info Attributes</span></span>  
 <span data-ttu-id="b3bcc-186">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="b3bcc-187">Kaynak kodu dosya yolu, kaynak kodu ve arayan üye adı satır numarasını edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="b3bcc-188">Üye arayan bilgileri almak için isteğe bağlı parametreler uygulanan öznitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="b3bcc-189">Her isteğe bağlı bir parametre varsayılan bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="b3bcc-190">Aşağıdaki tabloda tanımlanan arayan bilgileri öznitelikleri listeler <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="b3bcc-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="b3bcc-191">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b3bcc-191">Attribute</span></span>|<span data-ttu-id="b3bcc-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3bcc-192">Description</span></span>|<span data-ttu-id="b3bcc-193">Tür</span><span class="sxs-lookup"><span data-stu-id="b3bcc-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="b3bcc-194">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="b3bcc-195">Derleme zamanında yolu budur.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="b3bcc-196">Satır numarası kaynak dosyasındaki yöntemi adı verilir.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="b3bcc-197">Yöntem adı veya çağıranın özellik adı.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-197">Method name or property name of the caller.</span></span> <span data-ttu-id="b3bcc-198">Daha fazla bilgi için bkz: [arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="b3bcc-198">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="b3bcc-199">Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz: [arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="b3bcc-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bcc-200">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3bcc-200">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="b3bcc-201">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b3bcc-201">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b3bcc-202">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3bcc-202">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="b3bcc-203">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="b3bcc-203">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="b3bcc-204">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="b3bcc-204">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
