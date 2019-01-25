---
title: Ortak öznitelikler (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 4a1dd6200f7eb9e69caefe62d9e9defd90856ce1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558598"
---
# <a name="common-attributes-c"></a><span data-ttu-id="87afd-102">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="87afd-102">Common Attributes (C#)</span></span>
<span data-ttu-id="87afd-103">Bu konuda, C# programlarında en çok kullanılan öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87afd-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
-   [<span data-ttu-id="87afd-104">Genel Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87afd-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="87afd-105">Geçersiz öznitelik</span><span class="sxs-lookup"><span data-stu-id="87afd-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="87afd-106">Conditional özniteliği</span><span class="sxs-lookup"><span data-stu-id="87afd-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="87afd-107">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="87afd-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
##  <a name="Global"></a> <span data-ttu-id="87afd-108">Genel Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87afd-108">Global Attributes</span></span>  
 <span data-ttu-id="87afd-109">Çoğu öznitelik sınıfları veya yöntemleri gibi belirli dil öğelerini uygulanır; Ancak, bazı öznitelikler genel — bir tüm derleme veya modül için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="87afd-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="87afd-110">Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği, böyle bir derleme içinde sürüm bilgileri ekleme için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="87afd-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="87afd-111">Genel Öznitelikler görünen kaynak kodunda herhangi sonra en üst düzey `using` yönergeleri ve herhangi bir tür, modül veya ad alanı bildirimleri önce.</span><span class="sxs-lookup"><span data-stu-id="87afd-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="87afd-112">Genel Öznitelikler birden çok kaynak dosyalarında görünebilir, ancak dosyalar tek bir derleme pass derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="87afd-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="87afd-113">C# projelerinde, genel öznitelikler AssemblyInfo.cs dosyasında yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="87afd-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="87afd-114">Derleme özniteliklerinin bir derlemeyle ilgili bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="87afd-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="87afd-115">Bunlar, aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="87afd-115">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="87afd-116">Derleme kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="87afd-116">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="87afd-117">Bilgilendirme özniteliklerini</span><span class="sxs-lookup"><span data-stu-id="87afd-117">Informational attributes</span></span>  
  
-   <span data-ttu-id="87afd-118">Derleme bildirimi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="87afd-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="87afd-119">Derleme kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="87afd-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="87afd-120">Üç öznitelikler (katı bir adla, eğer varsa) bir derlemenin kimliğini belirler: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="87afd-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="87afd-121">Bu öznitelikler, bütünleştirilmiş kodun tam adı oluşturur ve kodda başvurduğunuzda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="87afd-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="87afd-122">Bir derlemenin sürüm ve kültür öznitelikleri kullanarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87afd-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="87afd-123">Ancak, Visual Studio IDE'de derleyici tarafından adı değeri ayarlanır [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box), veya Assembly Linker (Al.exe) derleme oluşturulduğunda derleme bildirimi içeren dosyada.</span><span class="sxs-lookup"><span data-stu-id="87afd-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="87afd-124"><xref:System.Reflection.AssemblyFlagsAttribute> Özniteliği, derlemenin birden fazla kopyası bulunabilir olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="87afd-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="87afd-125">Aşağıdaki tabloda, kimlik öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="87afd-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="87afd-126">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87afd-126">Attribute</span></span>|<span data-ttu-id="87afd-127">Amaç</span><span class="sxs-lookup"><span data-stu-id="87afd-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="87afd-128">Tam olarak bir derleme kimliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="87afd-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="87afd-129">Bir derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="87afd-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="87afd-130">Bu derlemenin desteklediği kültür belirtir.</span><span class="sxs-lookup"><span data-stu-id="87afd-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="87afd-131">Bir derlemeyi aynı işlemde ya da aynı uygulama etki alanında aynı bilgisayarda yan yana yürütme destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87afd-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="87afd-132">Bilgilendirme özniteliklerini</span><span class="sxs-lookup"><span data-stu-id="87afd-132">Informational Attributes</span></span>  
 <span data-ttu-id="87afd-133">Diğer şirket ya da bir derleme için ürün bilgi sağlamak için bilgilendirme özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87afd-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="87afd-134">Aşağıdaki tabloda tanımlanan bilgilendirme özniteliklerini gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="87afd-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="87afd-135">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87afd-135">Attribute</span></span>|<span data-ttu-id="87afd-136">Amaç</span><span class="sxs-lookup"><span data-stu-id="87afd-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="87afd-137">Bir derleme bildirimi için ürün adını belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87afd-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="87afd-138">Bir derleme bildirimi için bir ticari marka belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87afd-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="87afd-139">Bir derleme bildirimi için Bilgilendirme sürümü belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87afd-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="87afd-140">Bir derleme bildirimi için bir şirket adı belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87afd-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="87afd-141">Bir derleme bildirimi için telif hakkı belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87afd-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="87afd-142">Belirli bir sürüm numarasını için Win32 dosya sürüm kaynağının kullanılacağını derleyiciye.</span><span class="sxs-lookup"><span data-stu-id="87afd-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="87afd-143">Derleme ortak dil belirtimi (CLS) ile uyumlu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="87afd-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="87afd-144">Derleme bildirimi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="87afd-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="87afd-145">Derleme bildirimi bilgilerini sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87afd-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="87afd-146">Bu başlık, açıklama, varsayılan diğer ad ve yapılandırması içerir.</span><span class="sxs-lookup"><span data-stu-id="87afd-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="87afd-147">Aşağıdaki tabloda tanımlanan derleme bildirimi öznitelikleri gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="87afd-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="87afd-148">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87afd-148">Attribute</span></span>|<span data-ttu-id="87afd-149">Amaç</span><span class="sxs-lookup"><span data-stu-id="87afd-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="87afd-150">Bir derleme bildirimi derleme başlığını belirtir, özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87afd-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="87afd-151">Bir derleme bildirimi için bir derleme tanımı belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87afd-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="87afd-152">Bir derleme yapılandırmasını (örneğin, perakende veya hata ayıklama) belirten bir özel özniteliği için bir derleme bildirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87afd-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="87afd-153">Bir derleme bildirimi bir kolay varsayılan ad tanımlar</span><span class="sxs-lookup"><span data-stu-id="87afd-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="87afd-154">Geçersiz öznitelik</span><span class="sxs-lookup"><span data-stu-id="87afd-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="87afd-155">`Obsolete` Özniteliği bir program varlık, artık kullanılması olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="87afd-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="87afd-156">Artık kullanılmıyor olarak işaretlendiğinden bir varlığın her kullanımdan sonra bir uyarı veya öznitelik nasıl yapılandırıldığına bağlı olarak, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87afd-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="87afd-157">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="87afd-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="87afd-158">Bu örnekte `Obsolete` öznitelik sınıfına uygulanan `A` ve yönteme `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="87afd-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="87afd-159">Öznitelik oluşturucusunda ikinci bağımsız değişkeni için uyguladığı `B.OldMethod` ayarlanır `true`, sınıfını kullanarak ise bu yöntem bir derleyici hatasına neden olur `A` bir uyarı yalnızca üretim olur.</span><span class="sxs-lookup"><span data-stu-id="87afd-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="87afd-160">Çağırma `B.NewMethod`, ancak hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="87afd-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="87afd-161">Uyarı veya hata bir parçası olarak öznitelik yapıcısına ilk bağımsız değişken olarak sağlanan dizesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="87afd-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="87afd-162">Örneğin, önceki tanımları ile kullandığınızda, aşağıdaki kod iki uyarıları ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="87afd-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="87afd-163">Sınıf için iki uyarı `A` üretilir: sınıf başvurusu bildirimi için diğeri için sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="87afd-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="87afd-164">`Obsolete` Öznitelik bağımsız değişkeni olmadan kullanılabilir, ancak öğe neden dahil olmak üzere bir açıklama kullanılmıyor ve ne kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="87afd-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="87afd-165">`Obsolete` Özniteliği tek kullanımlık bir özniteliktir ve öznitelikleri izin veren herhangi bir varlık için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="87afd-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="87afd-166">`Obsolete` için bir diğer addır <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="87afd-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="87afd-167">Conditional özniteliği</span><span class="sxs-lookup"><span data-stu-id="87afd-167">Conditional Attribute</span></span>  
 <span data-ttu-id="87afd-168">`Conditional` Özniteliği bir yönteminin yürütülmesi bir ön işleme tanımlayıcısı bağımlı yapar.</span><span class="sxs-lookup"><span data-stu-id="87afd-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="87afd-169">`Conditional` Özniteliği için bir diğer ad, <xref:System.Diagnostics.ConditionalAttribute>ve bir yöntem veya bir öznitelik sınıfı için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="87afd-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="87afd-170">Bu örnekte, `Conditional` etkinleştirmek veya program özel tanılama bilgilerinin görüntülenmesini devre dışı bırakmak için bir yönteme uygulanır:</span><span class="sxs-lookup"><span data-stu-id="87afd-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="87afd-171">Varsa `TRACE_ON` tanımlayıcı tanımlı değil, hiçbir İzleme çıktısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="87afd-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="87afd-172">`Conditional` Özniteliği ile kullanılan genellikle `DEBUG` izleme ve hata ayıklama derlemeleri ancak içinde olmayan sürüm yapıları, günlük özellikleri etkinleştirmek için tanımlayıcı şöyle:</span><span class="sxs-lookup"><span data-stu-id="87afd-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="87afd-173">Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, varlığı veya yokluğu belirtilen ön işleme sembolünün çağrı dahil mi, yoksa atlanmış mı olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="87afd-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="87afd-174">Simge tanımlanmışsa çağrısı bulunur; Aksi takdirde, çağrı atlanır.</span><span class="sxs-lookup"><span data-stu-id="87afd-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="87afd-175">Kullanarak `Conditional` bir olmamasına içinde yöntemleri kapsayan daha zarif ve hataya daha az seçenek `#if…#endif` blokları, şöyle:</span><span class="sxs-lookup"><span data-stu-id="87afd-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="87afd-176">Bir koşullu metot bir class veya struct bildiriminde bir yöntem olmalı ve bir dönüş değeri olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="87afd-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="87afd-177">Birden çok tanımlayıcılarla</span><span class="sxs-lookup"><span data-stu-id="87afd-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="87afd-178">Bir yöntemin birden fazla varsa `Conditional` öznitelikleri, yönteme bir çağrı ise dahil en az bir koşullu simgeleri tanımlanır (diğer bir deyişle, simgeler mantıksal veya işlecini kullanarak birbirine bağlıdır).</span><span class="sxs-lookup"><span data-stu-id="87afd-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="87afd-179">Bu örnekte, ya da varlığını `A` veya `B` bir yöntem çağrısında neden olur:</span><span class="sxs-lookup"><span data-stu-id="87afd-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="87afd-180">Mantıksal ve işlecini kullanarak simgeleri bağlama etkiyi elde etmek için seri koşullu yöntemler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87afd-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="87afd-181">Örneğin, ikinci yöntem aşağıdaki yalnızca her iki yürütecek `A` ve `B` tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="87afd-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="87afd-182">Koşullu öznitelik sınıfları ile kullanma</span><span class="sxs-lookup"><span data-stu-id="87afd-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="87afd-183">`Conditional` Özniteliği bir öznitelik sınıf tanımına da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="87afd-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="87afd-184">Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="87afd-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
##  <a name="CallerInfo"></a> <span data-ttu-id="87afd-185">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="87afd-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="87afd-186">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87afd-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="87afd-187">Kaynak kodu dosyasının yolu, satır numarası kaynak kodu ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87afd-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="87afd-188">Üye arayan bilgileri elde etmek için isteğe bağlı parametrelere uygulanan öznitelikler kullanın.</span><span class="sxs-lookup"><span data-stu-id="87afd-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="87afd-189">İsteğe bağlı her parametre varsayılan bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="87afd-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="87afd-190">Aşağıdaki tabloda tanımlanan arayan bilgisi öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="87afd-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="87afd-191">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87afd-191">Attribute</span></span>|<span data-ttu-id="87afd-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87afd-192">Description</span></span>|<span data-ttu-id="87afd-193">Tür</span><span class="sxs-lookup"><span data-stu-id="87afd-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="87afd-194">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="87afd-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="87afd-195">Derleme zamanında yolu budur.</span><span class="sxs-lookup"><span data-stu-id="87afd-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="87afd-196">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="87afd-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="87afd-197">Yöntem adı veya çağıranın özelliğinin adı.</span><span class="sxs-lookup"><span data-stu-id="87afd-197">Method name or property name of the caller.</span></span> <span data-ttu-id="87afd-198">Daha fazla bilgi için [arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="87afd-198">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="87afd-199">Arayan bilgisi öznitelikleri hakkında daha fazla bilgi için bkz: [arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="87afd-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87afd-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87afd-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="87afd-201">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="87afd-201">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="87afd-202">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87afd-202">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="87afd-203">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="87afd-203">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="87afd-204">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="87afd-204">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
