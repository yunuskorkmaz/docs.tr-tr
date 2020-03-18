---
title: Ortak Öznitelikler (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399758"
---
# <a name="common-attributes-c"></a><span data-ttu-id="e88ab-102">Ortak Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="e88ab-102">Common Attributes (C#)</span></span>
<span data-ttu-id="e88ab-103">Bu konu, C# programlarında en sık kullanılan öznitelikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
- [<span data-ttu-id="e88ab-104">Genel Özellikler</span><span class="sxs-lookup"><span data-stu-id="e88ab-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="e88ab-105">Eski Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e88ab-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="e88ab-106">Koşullu Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e88ab-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="e88ab-107">Arayan Bilgi Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e88ab-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
## <a name="Global"></a><span data-ttu-id="e88ab-108">Genel Özellikler</span><span class="sxs-lookup"><span data-stu-id="e88ab-108">Global Attributes</span></span>  
 <span data-ttu-id="e88ab-109">Özniteliklerin çoğu sınıflar veya yöntemler gibi belirli dil öğelerine uygulanır; ancak, bazı öznitelikler geneldir— tüm derleme veya modül için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="e88ab-110">Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> öznitelik sürüm bilgilerini aşağıdaki gibi bir derlemeye yerleştirmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e88ab-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="e88ab-111">Genel öznitelikler kaynak kodunda herhangi `using` bir üst düzey yönergeden sonra ve herhangi bir tür, modül veya ad alanı bildirimlerinden önce görünür.</span><span class="sxs-lookup"><span data-stu-id="e88ab-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="e88ab-112">Genel öznitelikler birden çok kaynak dosyada görünebilir, ancak dosyaların tek bir derleme geçişinde derlenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="e88ab-113">C# projelerinde, genel öznitelikler AssemblyInfo.cs dosyasına konur.</span><span class="sxs-lookup"><span data-stu-id="e88ab-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="e88ab-114">Derleme öznitelikleri, derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="e88ab-115">Aşağıdaki kategorilere ayrılırlar:</span><span class="sxs-lookup"><span data-stu-id="e88ab-115">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="e88ab-116">Montaj kimlik öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e88ab-116">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="e88ab-117">Bilgilendirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="e88ab-117">Informational attributes</span></span>  
  
- <span data-ttu-id="e88ab-118">Derleme bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e88ab-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="e88ab-119">Montaj Kimlik Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e88ab-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="e88ab-120">Üç öznitelik (varsa güçlü bir adla) bir derlemenin kimliğini belirler: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="e88ab-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="e88ab-121">Bu öznitelikler derlemenin tam adını oluşturur ve kodda başvuru yaptığınızda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="e88ab-122">Öznitelikleri kullanarak derlemenin sürümünü ve kültürünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e88ab-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="e88ab-123">Ancak, ad değeri derleyici tarafından ayarlanır, Assembly Information [Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box)Visual Studio IDE , veya Derleme Bağlayıcı (Al.exe) derleme bildirimi içeren dosyaya dayalı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e88ab-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="e88ab-124">Öznitelik, <xref:System.Reflection.AssemblyFlagsAttribute> derlemenin birden çok kopyasının bir arada bulunup bulunamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="e88ab-125">Aşağıdaki tablo kimlik özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="e88ab-126">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e88ab-126">Attribute</span></span>|<span data-ttu-id="e88ab-127">Amaç</span><span class="sxs-lookup"><span data-stu-id="e88ab-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="e88ab-128">Bir derlemenin kimliğini tam olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="e88ab-129">Derlemenin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="e88ab-130">Derlemenin hangi kültürü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="e88ab-131">Derlemenin aynı bilgisayarda, aynı işlemde veya aynı uygulama etki alanında yan yana yürütmeyi destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="e88ab-132">Bilgi Özellikleri</span><span class="sxs-lookup"><span data-stu-id="e88ab-132">Informational Attributes</span></span>  
 <span data-ttu-id="e88ab-133">Bir derleme için ek şirket veya ürün bilgileri sağlamak için bilgi özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e88ab-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="e88ab-134">Aşağıdaki tabloda <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan bilgi öznitelikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="e88ab-135">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e88ab-135">Attribute</span></span>|<span data-ttu-id="e88ab-136">Amaç</span><span class="sxs-lookup"><span data-stu-id="e88ab-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="e88ab-137">Derleme bildirimi için bir ürün adı belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="e88ab-138">Derleme bildirimi için bir ticari marka belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="e88ab-139">Derleme bildirimi için bir bilgi sürümü belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="e88ab-140">Bir derleme bildirimi için şirket adını belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="e88ab-141">Derleme bildiriminin telif hakkını belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="e88ab-142">Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm numarası kullanmasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="e88ab-143">Derlemenin Ortak Dil Belirtimi (CLS) ile uyumlu olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="e88ab-144">Derleme Bildirimi Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e88ab-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="e88ab-145">Derleme bildiriminde bilgi sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e88ab-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="e88ab-146">Bu başlık, açıklama, varsayılan takma ad ve yapılandırma içerir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="e88ab-147">Aşağıdaki tablo, ad alanında tanımlanan <xref:System.Reflection?displayProperty=nameWithType> derleme bildirimi özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="e88ab-148">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e88ab-148">Attribute</span></span>|<span data-ttu-id="e88ab-149">Amaç</span><span class="sxs-lookup"><span data-stu-id="e88ab-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="e88ab-150">Derleme bildirimi için derleme başlığı belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="e88ab-151">Derleme bildirimi için derleme açıklaması belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="e88ab-152">Derleme bildirimi için derleme yapılandırması (perakende veya hata ayıklama gibi) belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e88ab-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="e88ab-153">Derleme bildirimi için uygun bir varsayılan takma ad tanımlar</span><span class="sxs-lookup"><span data-stu-id="e88ab-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a><span data-ttu-id="e88ab-154">Eski Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e88ab-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="e88ab-155">Öznitelik artık `Obsolete` kullanım için önerilen biri olarak bir program varlık işaretler.</span><span class="sxs-lookup"><span data-stu-id="e88ab-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="e88ab-156">Eski işaretlenmiş bir varlığın her kullanımı, özniteliğin nasıl yapılandırıldığına bağlı olarak daha sonra bir uyarı veya hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e88ab-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="e88ab-157">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e88ab-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="e88ab-158">Bu örnekte `Obsolete` öznitelik sınıfa `A` ve `B.OldMethod`yönteme uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e88ab-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="e88ab-159">Öznitelik oluşturucu uygulanan ikinci bağımsız `B.OldMethod` değişken için `true`ayarlanmış olduğundan, bu yöntem derleyici hatasına neden olurken, sınıf `A` kullanarak sadece bir uyarı üretecektir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="e88ab-160">Ancak `B.NewMethod`arama, hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="e88ab-161">Oluşturucuatörü atfetmek için ilk bağımsız değişken olarak sağlanan dize uyarı veya hatanın bir parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="e88ab-162">Örneğin, önceki tanımlarla kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e88ab-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="e88ab-163">Sınıf `A` için iki uyarı oluşturulur: biri sınıf başvuru bildirimi için, diğeri sınıf oluşturucusu için.</span><span class="sxs-lookup"><span data-stu-id="e88ab-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="e88ab-164">Öznitelik `Obsolete` bağımsız değişkenler olmadan kullanılabilir, ancak öğenin neden eski olduğu ve bunun yerine ne kullanılacağı bir açıklama da dahil olmak üzere önerilir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="e88ab-165">Öznitelik `Obsolete` tek kullanımlık bir özniteliktir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="e88ab-166">`Obsolete`<xref:System.ObsoleteAttribute>için bir takma addır.</span><span class="sxs-lookup"><span data-stu-id="e88ab-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a><span data-ttu-id="e88ab-167">Koşullu Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e88ab-167">Conditional Attribute</span></span>  
 <span data-ttu-id="e88ab-168">Öznitelik, `Conditional` bir yöntemin yürütülmesini bir ön işleme tanımlayıcısı bağımlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="e88ab-169">Öznitelik, `Conditional` <xref:System.Diagnostics.ConditionalAttribute>bir diğer adıdır ve bir yönteme veya öznitelik sınıfına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="e88ab-170">Bu örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı etmek için bir yöntem uygulanır:</span><span class="sxs-lookup"><span data-stu-id="e88ab-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="e88ab-171">`TRACE_ON` Tanımlayıcı tanımlanmamışsa, hiçbir izleme çıktısı görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="e88ab-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="e88ab-172">Öznitelik `Conditional` genellikle hata ayıklama yapılar için izleme ve günlük özelliklerini etkinleştirmek için tanımlayıcı ile `DEBUG` kullanılır, ancak sürüm yapılarda değil, aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="e88ab-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="e88ab-173">Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, belirtilen ön işleme sembolünün varlığı veya yokluğu çağrının dahil edilip edilmeyeceğini veya atlanıp atlanmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="e88ab-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="e88ab-174">Sembol tanımlanırsa, çağrı dahil edilir; aksi takdirde, arama atlanır.</span><span class="sxs-lookup"><span data-stu-id="e88ab-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="e88ab-175">Kullanma, `Conditional` daha temiz, daha zarif ve daha az hata `#if…#endif` yatkın bir alternatif blokların içinde yöntemleri çevreleyen, bu gibi:</span><span class="sxs-lookup"><span data-stu-id="e88ab-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="e88ab-176">Koşullu yöntem, bir sınıf veya yapı bildiriminde bir yöntem olmalı ve iade değerine sahip olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e88ab-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="e88ab-177">Birden Çok Tanımlayıcı Kullanma</span><span class="sxs-lookup"><span data-stu-id="e88ab-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="e88ab-178">Bir yöntemin `Conditional` birden çok özniteliği varsa, koşullu sembollerden en az biri tanımlanırsa (diğer bir deyişle, semboller OR işleci kullanılarak mantıksal olarak birbirine bağlanır).</span><span class="sxs-lookup"><span data-stu-id="e88ab-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="e88ab-179">Bu örnekte, ya `A` da `B` bir yöntem arama neden olur:</span><span class="sxs-lookup"><span data-stu-id="e88ab-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="e88ab-180">AND işleci kullanarak sembolleri mantıksal olarak bağlama efektini elde etmek için seri koşullu yöntemler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e88ab-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="e88ab-181">Örneğin, aşağıdaki ikinci yöntem yalnızca her `A` `B` ikisi de ve tanımlanmışsa yürütülecektir:</span><span class="sxs-lookup"><span data-stu-id="e88ab-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="e88ab-182">Öznitelik Sınıfları ile Koşullu Kullanma</span><span class="sxs-lookup"><span data-stu-id="e88ab-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="e88ab-183">Öznitelik, `Conditional` öznitelik sınıfı tanımına da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="e88ab-184">Bu örnekte, özel `Documentation` öznitelik yalnızca HATA Ayıklama tanımlanırsa meta verilere bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="e88ab-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
## <a name="CallerInfo"></a><span data-ttu-id="e88ab-185">Arayan Bilgi Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e88ab-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="e88ab-186">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e88ab-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="e88ab-187">Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e88ab-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="e88ab-188">Üye arayan bilgilerini elde etmek için isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e88ab-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="e88ab-189">Her isteğe bağlı parametre varsayılan değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="e88ab-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="e88ab-190">Aşağıdaki <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> tabloda, ad alanında tanımlanan Arayan Bilgileri öznitelikleri listelenir:</span><span class="sxs-lookup"><span data-stu-id="e88ab-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="e88ab-191">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e88ab-191">Attribute</span></span>|<span data-ttu-id="e88ab-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e88ab-192">Description</span></span>|<span data-ttu-id="e88ab-193">Tür</span><span class="sxs-lookup"><span data-stu-id="e88ab-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="e88ab-194">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="e88ab-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="e88ab-195">Bu derleme zamanda yoldur.</span><span class="sxs-lookup"><span data-stu-id="e88ab-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="e88ab-196">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="e88ab-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="e88ab-197">Arayanın yöntem adı veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="e88ab-197">Method name or property name of the caller.</span></span> <span data-ttu-id="e88ab-198">Daha fazla bilgi için [Bkz. Arayan Bilgileri (C#)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="e88ab-198">For more information, see [Caller Information (C#)](../caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="e88ab-199">Arayan Bilgileri öznitelikleri hakkında daha fazla bilgi [için, Bkz. Arayan Bilgileri (C#)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="e88ab-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e88ab-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e88ab-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="e88ab-201">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e88ab-201">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="e88ab-202">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e88ab-202">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="e88ab-203">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="e88ab-203">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="e88ab-204">Yansıma (C#) kullanarak Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="e88ab-204">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
