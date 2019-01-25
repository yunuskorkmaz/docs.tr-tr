---
title: Ortak öznitelikler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 0bc51a37fa0ccbcb3a74e1796686f0d6a6ec4d84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690910"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="c9ab2-102">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9ab2-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="c9ab2-103">Bu konuda, Visual Basic programlarında en çok kullanılan öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="c9ab2-104">Genel Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9ab2-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="c9ab2-105">Geçersiz öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9ab2-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="c9ab2-106">Conditional özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9ab2-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="c9ab2-107">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c9ab2-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="c9ab2-108">Visual Basic öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c9ab2-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <a name="Global"></a> <span data-ttu-id="c9ab2-109">Genel Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9ab2-109">Global Attributes</span></span>  
 <span data-ttu-id="c9ab2-110">Çoğu öznitelik sınıfları veya yöntemleri gibi belirli dil öğelerini uygulanır; Ancak, bazı öznitelikler genel — bir tüm derleme veya modül için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="c9ab2-111">Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği, böyle bir derleme içinde sürüm bilgileri ekleme için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="c9ab2-112">Genel Öznitelikler görünen kaynak kodunda herhangi sonra en üst düzey `Imports` deyimleri ve herhangi bir tür, modül veya ad alanı bildirimleri önce.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="c9ab2-113">Genel Öznitelikler birden çok kaynak dosyalarında görünebilir, ancak dosyalar tek bir derleme pass derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="c9ab2-114">Visual Basic projeleri için genel özniteliklerle (Visual Studio'da bir proje oluşturduğunuzda, dosyayı otomatik olarak oluşturulur) AssemblyInfo.vb dosyasında genellikle yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="c9ab2-115">Derleme özniteliklerinin bir derlemeyle ilgili bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="c9ab2-116">Bunlar, aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="c9ab2-117">Derleme kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c9ab2-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="c9ab2-118">Bilgilendirme özniteliklerini</span><span class="sxs-lookup"><span data-stu-id="c9ab2-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="c9ab2-119">Derleme bildirimi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c9ab2-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="c9ab2-120">Derleme kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c9ab2-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="c9ab2-121">Üç öznitelikler (katı bir adla, eğer varsa) bir derlemenin kimliğini belirler: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="c9ab2-122">Bu öznitelikler, bütünleştirilmiş kodun tam adı oluşturur ve kodda başvurduğunuzda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="c9ab2-123">Bir derlemenin sürüm ve kültür öznitelikleri kullanarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="c9ab2-124">Ancak, Visual Studio IDE'de derleyici tarafından adı değeri ayarlanır [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box), veya Assembly Linker (Al.exe) derleme oluşturulduğunda derleme bildirimi içeren dosyada.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="c9ab2-125"><xref:System.Reflection.AssemblyFlagsAttribute> Özniteliği, derlemenin birden fazla kopyası bulunabilir olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="c9ab2-126">Aşağıdaki tabloda, kimlik öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="c9ab2-127">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9ab2-127">Attribute</span></span>|<span data-ttu-id="c9ab2-128">Amaç</span><span class="sxs-lookup"><span data-stu-id="c9ab2-128">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="c9ab2-129">Tam olarak bir derleme kimliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-129">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="c9ab2-130">Bir derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-130">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="c9ab2-131">Bu derlemenin desteklediği kültür belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-131">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="c9ab2-132">Bir derlemeyi aynı işlemde ya da aynı uygulama etki alanında aynı bilgisayarda yan yana yürütme destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="c9ab2-133">Bilgilendirme özniteliklerini</span><span class="sxs-lookup"><span data-stu-id="c9ab2-133">Informational Attributes</span></span>  
 <span data-ttu-id="c9ab2-134">Diğer şirket ya da bir derleme için ürün bilgi sağlamak için bilgilendirme özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="c9ab2-135">Aşağıdaki tabloda tanımlanan bilgilendirme özniteliklerini gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="c9ab2-136">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9ab2-136">Attribute</span></span>|<span data-ttu-id="c9ab2-137">Amaç</span><span class="sxs-lookup"><span data-stu-id="c9ab2-137">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="c9ab2-138">Bir derleme bildirimi için ürün adını belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="c9ab2-139">Bir derleme bildirimi için bir ticari marka belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="c9ab2-140">Bir derleme bildirimi için Bilgilendirme sürümü belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="c9ab2-141">Bir derleme bildirimi için bir şirket adı belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="c9ab2-142">Bir derleme bildirimi için telif hakkı belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="c9ab2-143">Belirli bir sürüm numarasını için Win32 dosya sürüm kaynağının kullanılacağını derleyiciye.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="c9ab2-144">Derleme ortak dil belirtimi (CLS) ile uyumlu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="c9ab2-145">Derleme bildirimi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c9ab2-145">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="c9ab2-146">Derleme bildirimi bilgilerini sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="c9ab2-147">Bu başlık, açıklama, varsayılan diğer ad ve yapılandırması içerir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="c9ab2-148">Aşağıdaki tabloda tanımlanan derleme bildirimi öznitelikleri gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="c9ab2-149">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9ab2-149">Attribute</span></span>|<span data-ttu-id="c9ab2-150">Amaç</span><span class="sxs-lookup"><span data-stu-id="c9ab2-150">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="c9ab2-151">Bir derleme bildirimi derleme başlığını belirtir, özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="c9ab2-152">Bir derleme bildirimi için bir derleme tanımı belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="c9ab2-153">Bir derleme yapılandırmasını (örneğin, perakende veya hata ayıklama) belirten bir özel özniteliği için bir derleme bildirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="c9ab2-154">Bir derleme bildirimi bir kolay varsayılan ad tanımlar</span><span class="sxs-lookup"><span data-stu-id="c9ab2-154">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="c9ab2-155">Geçersiz öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9ab2-155">Obsolete Attribute</span></span>  
 <span data-ttu-id="c9ab2-156">`Obsolete` Özniteliği bir program varlık, artık kullanılması olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="c9ab2-157">Artık kullanılmıyor olarak işaretlendiğinden bir varlığın her kullanımdan sonra bir uyarı veya öznitelik nasıl yapılandırıldığına bağlı olarak, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="c9ab2-158">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-158">For example:</span></span>  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="c9ab2-159">Bu örnekte `Obsolete` öznitelik sınıfına uygulanan `A` ve yönteme `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="c9ab2-160">Öznitelik oluşturucusunda ikinci bağımsız değişkeni için uyguladığı `B.OldMethod` ayarlanır `true`, sınıfını kullanarak ise bu yöntem bir derleyici hatasına neden olur `A` bir uyarı yalnızca üretim olur.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="c9ab2-161">Çağırma `B.NewMethod`, ancak hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="c9ab2-162">Uyarı veya hata bir parçası olarak öznitelik yapıcısına ilk bağımsız değişken olarak sağlanan dizesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="c9ab2-163">Örneğin, önceki tanımları ile kullandığınızda, aşağıdaki kod iki uyarıları ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="c9ab2-164">Sınıf için iki uyarı `A` üretilir: sınıf başvurusu bildirimi için diğeri için sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="c9ab2-165">`Obsolete` Öznitelik bağımsız değişkeni olmadan kullanılabilir, ancak öğe neden dahil olmak üzere bir açıklama kullanılmıyor ve ne kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="c9ab2-166">`Obsolete` Özniteliği tek kullanımlık bir özniteliktir ve öznitelikleri izin veren herhangi bir varlık için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="c9ab2-167">`Obsolete` için bir diğer addır <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="c9ab2-168">Conditional özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9ab2-168">Conditional Attribute</span></span>  
 <span data-ttu-id="c9ab2-169">`Conditional` Özniteliği bir yönteminin yürütülmesi bir ön işleme tanımlayıcısı bağımlı yapar.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="c9ab2-170">`Conditional` Özniteliği için bir diğer ad, <xref:System.Diagnostics.ConditionalAttribute>ve bir yöntem veya bir öznitelik sınıfı için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="c9ab2-171">Bu örnekte, `Conditional` etkinleştirmek veya program özel tanılama bilgilerinin görüntülenmesini devre dışı bırakmak için bir yönteme uygulanır:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c9ab2-172">Varsa `TRACE_ON` tanımlayıcı tanımlı değil, hiçbir İzleme çıktısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="c9ab2-173">`Conditional` Özniteliği ile kullanılan genellikle `DEBUG` izleme ve hata ayıklama derlemeleri ancak içinde olmayan sürüm yapıları, günlük özellikleri etkinleştirmek için tanımlayıcı şöyle:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="c9ab2-174">Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, varlığı veya yokluğu belirtilen ön işleme sembolünün çağrı dahil mi, yoksa atlanmış mı olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="c9ab2-175">Simge tanımlanmışsa çağrısı bulunur; Aksi takdirde, çağrı atlanır.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="c9ab2-176">Kullanarak `Conditional` bir olmamasına içinde yöntemleri kapsayan daha zarif ve hataya daha az seçenek `#if…#endif` blokları, şöyle:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="c9ab2-177">Bir koşullu metot bir class veya struct bildiriminde bir yöntem olmalı ve bir dönüş değeri olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="c9ab2-178">Birden çok tanımlayıcılarla</span><span class="sxs-lookup"><span data-stu-id="c9ab2-178">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="c9ab2-179">Bir yöntemin birden fazla varsa `Conditional` öznitelikleri, yönteme bir çağrı ise dahil en az bir koşullu simgeleri tanımlanır (diğer bir deyişle, simgeler mantıksal veya işlecini kullanarak birbirine bağlıdır).</span><span class="sxs-lookup"><span data-stu-id="c9ab2-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="c9ab2-180">Bu örnekte, ya da varlığını `A` veya `B` bir yöntem çağrısında neden olur:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="c9ab2-181">Mantıksal ve işlecini kullanarak simgeleri bağlama etkiyi elde etmek için seri koşullu yöntemler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="c9ab2-182">Örneğin, ikinci yöntem aşağıdaki yalnızca her iki yürütecek `A` ve `B` tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="c9ab2-183">Koşullu öznitelik sınıfları ile kullanma</span><span class="sxs-lookup"><span data-stu-id="c9ab2-183">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="c9ab2-184">`Conditional` Özniteliği bir öznitelik sınıf tanımına da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="c9ab2-185">Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <a name="CallerInfo"></a> <span data-ttu-id="c9ab2-186">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c9ab2-186">Caller Info Attributes</span></span>  
 <span data-ttu-id="c9ab2-187">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="c9ab2-188">Kaynak kodu dosyasının yolu, satır numarası kaynak kodu ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="c9ab2-189">Üye arayan bilgileri elde etmek için isteğe bağlı parametrelere uygulanan öznitelikler kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="c9ab2-190">İsteğe bağlı her parametre varsayılan bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="c9ab2-191">Aşağıdaki tabloda tanımlanan arayan bilgisi öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="c9ab2-192">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9ab2-192">Attribute</span></span>|<span data-ttu-id="c9ab2-193">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9ab2-193">Description</span></span>|<span data-ttu-id="c9ab2-194">Tür</span><span class="sxs-lookup"><span data-stu-id="c9ab2-194">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="c9ab2-195">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="c9ab2-196">Derleme zamanında yolu budur.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-196">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="c9ab2-197">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-197">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="c9ab2-198">Yöntem adı veya çağıranın özelliğinin adı.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-198">Method name or property name of the caller.</span></span> <span data-ttu-id="c9ab2-199">Daha fazla bilgi için [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="c9ab2-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="c9ab2-200">Arayan bilgisi öznitelikleri hakkında daha fazla bilgi için bkz: [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="c9ab2-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <a name="VB"></a> <span data-ttu-id="c9ab2-201">Visual Basic öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c9ab2-201">Visual Basic Attributes</span></span>  
 <span data-ttu-id="c9ab2-202">Aşağıdaki tabloda, Visual Basic özel özniteliklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-202">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="c9ab2-203">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9ab2-203">Attribute</span></span>|<span data-ttu-id="c9ab2-204">Amaç</span><span class="sxs-lookup"><span data-stu-id="c9ab2-204">Purpose</span></span>|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="c9ab2-205">Derleyiciye, sınıfı bir COM nesnesi olarak açılmamalıdır gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="c9ab2-206">Modül üyelerinin yalnızca modül için gerekli nitelik kullanılarak erişilecektir izin verir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="c9ab2-207">Bir sabit uzunluklu dize boyutu kullanmak için bir yapı ile giriş ve çıkış dosyasını belirtir. işlevleri.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="c9ab2-208">Sabit bir dizinin boyutu kullanmak için bir yapı ile giriş ve çıkış dosyasını belirtir. işlevleri.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="c9ab2-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="c9ab2-209">COMClassAttribute</span></span>  
 <span data-ttu-id="c9ab2-210">Kullanım `COMClassAttribute` Visual Basic'den COM bileşenleri oluşturma işlemini basitleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="c9ab2-211">COM nesneleri, .NET Framework derlemeleri ve olmadan önemli ölçüde farklı `COMClassAttribute`, çeşitli Visual Basic'den COM nesnesi oluşturmak için adımları izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="c9ab2-212">İşaretlenmiş sınıflar için `COMClassAttribute`, derleyici bu adımların birçoğunun otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="c9ab2-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="c9ab2-213">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="c9ab2-214">Kullanım `HideModuleNameAttribute` modülü üyeleri yalnızca modül için gerekli nitelik kullanılarak erişilecek izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="c9ab2-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="c9ab2-215">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="c9ab2-216">Kullanım `VBFixedStringAttribute` sabit uzunluklu bir dize oluşturmak için Visual Basic zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="c9ab2-217">Varsayılan olarak, değişken uzunluğu dizelerdir ve bu öznitelik dosyaları dizelere depolarken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="c9ab2-218">Aşağıdaki kod bunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c9ab2-218">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="c9ab2-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="c9ab2-219">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="c9ab2-220">Kullanım `VBFixedArrayAttribute` sabit boyutludur diziler bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="c9ab2-221">Visual Basic dizeleri gibi varsayılan olarak, değişken uzunluğu dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="c9ab2-222">Bu öznitelik serileştirilmesi ya da veri dosyalara yazma kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-222">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ab2-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9ab2-223">See also</span></span>
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="c9ab2-224">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c9ab2-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="c9ab2-225">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9ab2-225">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="c9ab2-226">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9ab2-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="c9ab2-227">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="c9ab2-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
