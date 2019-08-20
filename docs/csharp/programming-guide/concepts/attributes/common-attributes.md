---
title: Ortak öznitelikler (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595466"
---
# <a name="common-attributes-c"></a><span data-ttu-id="31c65-102">Ortak öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="31c65-102">Common Attributes (C#)</span></span>
<span data-ttu-id="31c65-103">Bu konuda, C# programlarda en yaygın olarak kullanılan öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31c65-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
- [<span data-ttu-id="31c65-104">Genel öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31c65-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="31c65-105">Kullanımdan kaldırılmış öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c65-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="31c65-106">Koşullu öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c65-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="31c65-107">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="31c65-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
## <a name="Global"></a><span data-ttu-id="31c65-108">Genel öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31c65-108">Global Attributes</span></span>  
 <span data-ttu-id="31c65-109">Çoğu öznitelik sınıflar veya yöntemler gibi belirli dil öğelerine uygulanır; Ancak, bazı öznitelikler geneldir, tüm derleme veya modül için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="31c65-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="31c65-110">Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği aşağıdaki gibi bir derlemeye sürüm bilgisi eklemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="31c65-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="31c65-111">Genel öznitelikler, herhangi bir üst düzey `using` yönergelerden sonra ve herhangi bir tür, modül veya ad alanı bildirimlerinden sonra kaynak kodunda görünür.</span><span class="sxs-lookup"><span data-stu-id="31c65-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="31c65-112">Genel öznitelikler birden çok kaynak dosyasında görünebilir, ancak dosyaların tek bir derleme geçişinde derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="31c65-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="31c65-113">C# Projelerde, genel öznitelikler AssemblyInfo.cs dosyasına konur.</span><span class="sxs-lookup"><span data-stu-id="31c65-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="31c65-114">Derleme öznitelikleri, bir derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="31c65-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="31c65-115">Bunlar aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="31c65-115">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="31c65-116">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="31c65-116">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="31c65-117">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31c65-117">Informational attributes</span></span>  
  
- <span data-ttu-id="31c65-118">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="31c65-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="31c65-119">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="31c65-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="31c65-120">Üç öznitelik (varsa, güçlü bir ad varsa) bir derlemenin kimliğini belirleme: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="31c65-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="31c65-121">Bu öznitelikler, derlemenin tam adını oluşturur ve kodda başvuru yaptığınızda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31c65-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="31c65-122">Öznitelikleri kullanarak bir derlemenin sürümünü ve kültürünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31c65-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="31c65-123">Bununla birlikte, ad değeri derleyici tarafından, derleme [bilgileri Iletişim kutusunda](/visualstudio/ide/reference/assembly-information-dialog-box)VISUAL Studio IDE veya derleme oluşturulduğunda derleme Bağlayıcısı (al. exe) tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="31c65-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="31c65-124"><xref:System.Reflection.AssemblyFlagsAttribute> Özniteliği, derlemenin birden çok kopyasının birlikte kullanılıp kullanılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="31c65-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="31c65-125">Aşağıdaki tabloda kimlik öznitelikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31c65-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="31c65-126">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c65-126">Attribute</span></span>|<span data-ttu-id="31c65-127">Amaç</span><span class="sxs-lookup"><span data-stu-id="31c65-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="31c65-128">Bir derlemenin kimliğini tam olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="31c65-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="31c65-129">Bir derlemenin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="31c65-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="31c65-130">Derlemenin desteklediği kültürü belirtir.</span><span class="sxs-lookup"><span data-stu-id="31c65-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="31c65-131">Bir derlemenin aynı bilgisayarda, aynı işlemde veya aynı uygulama etki alanında yan yana yürütmeyi destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="31c65-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="31c65-132">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31c65-132">Informational Attributes</span></span>  
 <span data-ttu-id="31c65-133">Bir derlemeye ek şirket veya ürün bilgileri sağlamak için bilgilendirici öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31c65-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="31c65-134">Aşağıdaki tabloda, <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan bilgilendirici öznitelikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31c65-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="31c65-135">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c65-135">Attribute</span></span>|<span data-ttu-id="31c65-136">Amaç</span><span class="sxs-lookup"><span data-stu-id="31c65-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="31c65-137">Bir derleme bildirimi için bir ürün adı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="31c65-138">Bir derleme bildirimi için ticari marka belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="31c65-139">Bir derleme bildirimi için bilgilendirici bir sürüm belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="31c65-140">Bir derleme bildirimi için bir şirket adı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="31c65-141">Bir derleme bildirimi için bir telif hakkı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="31c65-142">Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm numarası kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="31c65-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="31c65-143">Derlemenin ortak dil belirtimi (CLS) ile uyumlu olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31c65-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="31c65-144">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="31c65-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="31c65-145">Derleme bildiriminde bilgi sağlamak için bütünleştirilmiş kod bildirim özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31c65-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="31c65-146">Buna Başlık, açıklama, varsayılan diğer ad ve yapılandırma dahildir.</span><span class="sxs-lookup"><span data-stu-id="31c65-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="31c65-147">Aşağıdaki tabloda, <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan derleme bildirimi öznitelikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31c65-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="31c65-148">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c65-148">Attribute</span></span>|<span data-ttu-id="31c65-149">Amaç</span><span class="sxs-lookup"><span data-stu-id="31c65-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="31c65-150">Bir derleme bildirimi için derleme başlığını belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="31c65-151">Bir derleme bildirimi için derleme açıklamasını belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="31c65-152">Derleme bildirimi için bir derleme yapılandırması (perakende veya hata ayıklama) belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="31c65-153">Bir derleme bildirimi için kolay bir varsayılan diğer ad tanımlar</span><span class="sxs-lookup"><span data-stu-id="31c65-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a><span data-ttu-id="31c65-154">Kullanımdan kaldırılmış öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c65-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="31c65-155">Özniteliği `Obsolete` , bir program varlığını artık kullanım için önerilmeyen bir şekilde işaretler.</span><span class="sxs-lookup"><span data-stu-id="31c65-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="31c65-156">Kullanımdan kalktı olarak işaretlenen bir varlığın her kullanımı, özniteliğin nasıl yapılandırıldığına bağlı olarak bir uyarı veya hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31c65-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="31c65-157">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="31c65-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="31c65-158">Bu örnekte, `Obsolete` özniteliği sınıfa `A` ve yöntemine `B.OldMethod`uygulanır.</span><span class="sxs-lookup"><span data-stu-id="31c65-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="31c65-159">Öğesine `B.OldMethod` uygulanan öznitelik oluşturucusunun ikinci bağımsız değişkeni olarak `true`ayarlandığından, bu yöntem bir derleyici hatasına neden olur, ancak sınıf `A` kullanımı yalnızca bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31c65-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="31c65-160">Ancak `B.NewMethod`çağırma, hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="31c65-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="31c65-161">Öznitelik oluşturucusuna ilk bağımsız değişken olarak girilen dize, uyarının veya hatanın bir parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="31c65-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="31c65-162">Örneğin, önceki tanımlarla birlikte kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="31c65-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="31c65-163">Sınıf `A` için iki uyarı oluşturulur: biri sınıf başvurusunun bildirimi ve diğeri sınıf oluşturucusu içindir.</span><span class="sxs-lookup"><span data-stu-id="31c65-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="31c65-164">`Obsolete` Öznitelik bağımsız değişkenler olmadan kullanılabilir, ancak öğenin neden kullanımdan kalkdığına ve bunun yerine ne tür bir açıklama dahil edilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="31c65-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="31c65-165">`Obsolete` Özniteliği tek kullanım özniteliğidir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="31c65-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="31c65-166">`Obsolete`, için <xref:System.ObsoleteAttribute>bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="31c65-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a><span data-ttu-id="31c65-167">Koşullu öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c65-167">Conditional Attribute</span></span>  
 <span data-ttu-id="31c65-168">`Conditional` Özniteliği bir işlem ön işleme tanımlayıcısına bağımlı bir yöntemin yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="31c65-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="31c65-169">`Conditional` Özniteliği için<xref:System.Diagnostics.ConditionalAttribute>bir diğer addır ve bir yönteme veya öznitelik sınıfına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="31c65-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="31c65-170">Bu örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı bırakmak için bir yönteme uygulanır:</span><span class="sxs-lookup"><span data-stu-id="31c65-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="31c65-171">`TRACE_ON` Tanımlayıcı tanımlanmamışsa, hiçbir izleme çıkışı gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="31c65-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="31c65-172">Öznitelik, genellikle hata ayıklama derlemeleri için `DEBUG` izleme ve günlüğe kaydetme özelliklerini etkinleştirmek için tanımlayıcı ile birlikte kullanılır, ancak bunun gibi sürüm yapılarında desteklenmez: `Conditional`</span><span class="sxs-lookup"><span data-stu-id="31c65-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="31c65-173">Koşullu olarak işaretlenen bir yöntem çağrıldığında, belirtilen ön işleme simgesinin varlığı veya yokluğu, çağrının eklenip eklenmeyeceğini veya atlanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="31c65-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="31c65-174">Sembol tanımlanmışsa, çağrı dahil edilir; Aksi takdirde, çağrı atlanır.</span><span class="sxs-lookup"><span data-stu-id="31c65-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="31c65-175">Kullanılarak `Conditional` , blokların içindeki yöntemlerin içine yerleştirilmesi `#if…#endif` için aşağıdaki gibi bir temizleyici, daha zarif ve daha az hataya açık bir alternatiftir:</span><span class="sxs-lookup"><span data-stu-id="31c65-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="31c65-176">Koşullu Yöntem bir sınıf veya yapı bildiriminde bir yöntem olmalıdır ve dönüş değeri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="31c65-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="31c65-177">Birden çok tanımlayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="31c65-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="31c65-178">Bir yöntemin birden çok `Conditional` özniteliği varsa, koşullu simgelerden en az biri tanımlanmışsa yöntemine bir çağrı dahil edilir (başka bir deyişle, semboller or işleci kullanılarak mantıksal olarak birbirlerine bağlanır).</span><span class="sxs-lookup"><span data-stu-id="31c65-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="31c65-179">Bu örnekte, ya da `A` `B` birinin varlığı bir yöntem çağrısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="31c65-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="31c65-180">VE işlecini kullanarak sembolleri mantıksal olarak bağlama etkisini elde etmek için, seri koşullu yöntemleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31c65-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="31c65-181">Örneğin, aşağıdaki ikinci yöntem yalnızca `A` ve `B` tanımlanırsa yürütülür:</span><span class="sxs-lookup"><span data-stu-id="31c65-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="31c65-182">Öznitelik sınıfları ile koşullu kullanma</span><span class="sxs-lookup"><span data-stu-id="31c65-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="31c65-183">Öznitelik `Conditional` , öznitelik sınıfı tanımına da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="31c65-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="31c65-184">Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="31c65-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
## <a name="CallerInfo"></a><span data-ttu-id="31c65-185">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="31c65-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="31c65-186">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31c65-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="31c65-187">Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31c65-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="31c65-188">Üye çağıran bilgilerini almak için, isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="31c65-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="31c65-189">Her isteğe bağlı parametre varsayılan bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="31c65-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="31c65-190">Aşağıdaki tabloda, <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="31c65-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="31c65-191">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c65-191">Attribute</span></span>|<span data-ttu-id="31c65-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31c65-192">Description</span></span>|<span data-ttu-id="31c65-193">Tür</span><span class="sxs-lookup"><span data-stu-id="31c65-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="31c65-194">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="31c65-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="31c65-195">Bu, derleme zamanının yoludur.</span><span class="sxs-lookup"><span data-stu-id="31c65-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="31c65-196">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="31c65-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="31c65-197">Çağıranın Yöntem adı veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="31c65-197">Method name or property name of the caller.</span></span> <span data-ttu-id="31c65-198">Daha fazla bilgi için bkz. [arayan bilgileriC#()](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="31c65-198">For more information, see [Caller Information (C#)](../caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="31c65-199">Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz. [arayan bilgileri (C#)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="31c65-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c65-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31c65-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="31c65-201">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="31c65-201">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="31c65-202">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31c65-202">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="31c65-203">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="31c65-203">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="31c65-204">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="31c65-204">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
