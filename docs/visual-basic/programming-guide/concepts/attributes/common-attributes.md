---
title: "Ortak öznitelikler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4781e7ee60017455796d460d8d7bddb9f7c49676
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="643b7-102">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="643b7-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="643b7-103">Bu konuda, Visual Basic programlarında en yaygın olarak kullanılan öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="643b7-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="643b7-104">Genel Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="643b7-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="643b7-105">Artık kullanılmayan özniteliği</span><span class="sxs-lookup"><span data-stu-id="643b7-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="643b7-106">Koşul özniteliği</span><span class="sxs-lookup"><span data-stu-id="643b7-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="643b7-107">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="643b7-108">Visual Basic öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <span data-ttu-id="643b7-109"><a name="Global"></a>Genel Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="643b7-109"><a name="Global"></a> Global Attributes</span></span>  
 <span data-ttu-id="643b7-110">Çoğu öznitelik sınıfları veya yöntemleri gibi belirli bir dil öğeleri uygulanır; Ancak, bazı öznitelikler genel — tüm derleme veya modülü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="643b7-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="643b7-111">Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği, böyle bir bütünleştirilmiş sürüm bilgilerini eklemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="643b7-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="643b7-112">Genel Öznitelikler görünen kaynak kodunda herhangi sonra en üst düzey `Imports` deyimleri ve herhangi bir tür, modül veya ad alanı bildirimleri öncesinde.</span><span class="sxs-lookup"><span data-stu-id="643b7-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="643b7-113">Genel Öznitelikler birden çok kaynak dosyalarında görünebilir, ancak dosyaları tek bir derleme geçişinde derlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="643b7-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="643b7-114">Visual Basic projeleri için genel özniteliklerle (Visual Studio'da bir proje oluşturduğunuzda dosyası otomatik olarak oluşturulur) AssemblyInfo.vb dosyasında genellikle yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="643b7-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="643b7-115">Derleme özniteliklerinin bir derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="643b7-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="643b7-116">Bunlar aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="643b7-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="643b7-117">Derleme kimlik öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="643b7-118">Bilgilendirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="643b7-119">Derleme bildirimi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="643b7-120">Derleme kimlik öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="643b7-121">Üç özniteliklerle (tanımlayıcı ad, eğer varsa) bir derleme kimliğini belirlemek: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="643b7-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="643b7-122">Bu öznitelikler derlemenin tam adını formunu ve kodda başvurduğunuzda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="643b7-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="643b7-123">Bir derlemenin sürüm ve öznitelikleri kullanarak kültür ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643b7-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="643b7-124">Ancak, ad değeri Visual Studio IDE içinde derleyici tarafından ayarlanır [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box), ya da derleme bağlayıcı (derleme oluşturulduğunda Al.exe) derleme bildirimi içeren dosyayı alarak.</span><span class="sxs-lookup"><span data-stu-id="643b7-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="643b7-125"><xref:System.Reflection.AssemblyFlagsAttribute> Özniteliği, derleme birden çok kopyasını bir arada var olabilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="643b7-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="643b7-126">Aşağıdaki tabloda kimlik öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="643b7-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="643b7-127">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="643b7-127">Attribute</span></span>|<span data-ttu-id="643b7-128">Amaç</span><span class="sxs-lookup"><span data-stu-id="643b7-128">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="643b7-129">Tam olarak bir derleme kimliğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="643b7-129">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="643b7-130">Bir derlemeyi sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="643b7-130">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="643b7-131">Hangi derleme destekler kültür belirtir.</span><span class="sxs-lookup"><span data-stu-id="643b7-131">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="643b7-132">Bir derlemeyi aynı bilgisayardaki aynı işlemde ya da aynı uygulama etki alanında yan yana yürütme destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="643b7-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="643b7-133">Bilgilendirme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-133">Informational Attributes</span></span>  
 <span data-ttu-id="643b7-134">Bilgilendirme öznitelikleri, ek şirket veya bir derleme için ürün bilgi sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643b7-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="643b7-135">Aşağıdaki tabloda tanımlanan bilgilendirme öznitelikleri gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="643b7-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="643b7-136">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="643b7-136">Attribute</span></span>|<span data-ttu-id="643b7-137">Amaç</span><span class="sxs-lookup"><span data-stu-id="643b7-137">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="643b7-138">Derleme bildirimi ürün adını belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="643b7-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="643b7-139">Derleme bildirimi için bir ticari marka belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="643b7-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="643b7-140">Derleme bildirimi için bilgilendirici bir sürümünü belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="643b7-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="643b7-141">Derleme bildirimi için bir şirket adı belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="643b7-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="643b7-142">Derleme bildirimi için telif hakkı belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="643b7-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="643b7-143">Derleyicinin Win32 dosya sürümü kaynak için belirli bir sürüm numarasını kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="643b7-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="643b7-144">Derleme ortak dil belirtimi (CLS) ile uyumlu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="643b7-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="643b7-145">Derleme bildirimi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-145">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="643b7-146">Derleme bildirimi özniteliklerinin derleme bildirimi bilgi sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643b7-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="643b7-147">Bu başlık, açıklama, varsayılan diğer ad ve yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="643b7-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="643b7-148">Derleme bildirimi öznitelikleri tanımlanan aşağıdaki tabloda gösterilmektedir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="643b7-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="643b7-149">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="643b7-149">Attribute</span></span>|<span data-ttu-id="643b7-150">Amaç</span><span class="sxs-lookup"><span data-stu-id="643b7-150">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="643b7-151">Derleme bildirimi için bir derleme başlık belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="643b7-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="643b7-152">Derleme bildirimi derleme açıklamasını belirtir özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="643b7-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="643b7-153">Bir derleme yapılandırmasını (örneğin, tekil veya hata ayıklama) belirten özel bir öznitelik için bir derleme bildirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="643b7-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="643b7-154">Derleme bildirimi için bir kolay varsayılan diğer adı tanımlar</span><span class="sxs-lookup"><span data-stu-id="643b7-154">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <span data-ttu-id="643b7-155"><a name="Obsolete"></a>Artık kullanılmayan özniteliği</span><span class="sxs-lookup"><span data-stu-id="643b7-155"><a name="Obsolete"></a> Obsolete Attribute</span></span>  
 <span data-ttu-id="643b7-156">`Obsolete` Özniteliği bir program varlık artık kullanım için önerilen biri olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="643b7-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="643b7-157">Artık kullanılmayan olarak işaretlenmiş bir varlığın her kullanın, daha sonra bir uyarı veya öznitelik nasıl yapılandırıldığına bağlı olarak bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="643b7-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="643b7-158">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="643b7-158">For example:</span></span>  
  
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
  
 <span data-ttu-id="643b7-159">Bu örnekte `Obsolete` özniteliği sınıfına uygulanan `A` ve yöntemine `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="643b7-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="643b7-160">Öznitelik oluşturucunun ikinci bağımsız değişkeni uygulanan çünkü `B.OldMethod` ayarlanır `true`, bu yöntem, sınıfını kullanarak ancak derleyici hatası neden olur `A` bir uyarı yalnızca ürettiği olur.</span><span class="sxs-lookup"><span data-stu-id="643b7-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="643b7-161">Çağırma `B.NewMethod`, ancak hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="643b7-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="643b7-162">Öznitelik oluşturucunun ilk bağımsız değişkeni olarak sağlanan dize uyarı veya hata bir parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="643b7-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="643b7-163">Örneğin, önceki tanımları ile kullandığınızda, aşağıdaki kod iki uyarılar ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="643b7-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="643b7-164">Sınıfı için iki uyarıları `A` oluşturulur: sınıf başvurusu bildirimi için diğeri için sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="643b7-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="643b7-165">`Obsolete` Öznitelik bağımsız değişkenler olmadan kullanılabilir, ancak neden bir açıklaması da dahil olmak üzere öğe kullanılmıyor ve ne kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="643b7-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="643b7-166">`Obsolete` Özniteliği bir tek kullanımlık özniteliği ve öznitelikleri veren herhangi bir varlık için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="643b7-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="643b7-167">`Obsolete`bir diğer adı için <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="643b7-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <span data-ttu-id="643b7-168"><a name="Conditional"></a>Koşul özniteliği</span><span class="sxs-lookup"><span data-stu-id="643b7-168"><a name="Conditional"></a> Conditional Attribute</span></span>  
 <span data-ttu-id="643b7-169">`Conditional` Özniteliği bir yönteminin yürütülmesi üzerinde önişlem tanımlayıcısını bağımlı yapar.</span><span class="sxs-lookup"><span data-stu-id="643b7-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="643b7-170">`Conditional` Özniteliktir için diğer ad <xref:System.Diagnostics.ConditionalAttribute>ve bir yöntem veya öznitelik sınıfı için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="643b7-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="643b7-171">Bu örnekte, `Conditional` etkinleştirmek veya programa özgü tanı bilgilerini görüntülemeyi devre dışı bırakmak için bir yönteme uygulanır:</span><span class="sxs-lookup"><span data-stu-id="643b7-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="643b7-172">Varsa `TRACE_ON` tanımlayıcısı tanımlı değil, izleme çıktısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="643b7-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="643b7-173">`Conditional` Özniteliği ile kullanılan genellikle `DEBUG` izleme ve hata ayıklama derlemeleri ancak içinde değil yayın derlemeler, günlük özellikleri etkinleştirmek için tanımlayıcı şöyle:</span><span class="sxs-lookup"><span data-stu-id="643b7-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="643b7-174">Koşullu olarak işaretli bir yöntem çağrıldığında, varlığının veya yokluğunun belirtilen önişlem simgenin çağrı dahil atlanmış verilip verilmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="643b7-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="643b7-175">Simgenin tanımlanmışsa, çağrı bulunur; Aksi halde çağrı atlanır.</span><span class="sxs-lookup"><span data-stu-id="643b7-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="643b7-176">Kullanarak `Conditional` bir temizleyici olan yöntemleri içinde kapsayan daha zarif ve hataya daha az alternatif `#if…#endif` blokları, şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="643b7-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="643b7-177">Koşullu bir yöntem sınıfta veya yapı bildiriminde bir yöntem olmalıdır ve bir dönüş değeri olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="643b7-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="643b7-178">Birden çok tanımlayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="643b7-178">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="643b7-179">Bir yöntemin birden çok varsa `Conditional` öznitelikleri yöntemine bir çağrı dahil en az bir koşullu simgelerin tanımlanmışsa (diğer bir deyişle, simgeler mantıksal veya işlecini kullanarak birbirine bağlıdır).</span><span class="sxs-lookup"><span data-stu-id="643b7-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="643b7-180">Bu örnekte, ya da varlığını `A` veya `B` bir yöntem çağrısı neden olur:</span><span class="sxs-lookup"><span data-stu-id="643b7-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="643b7-181">Mantıksal ve işlecini kullanarak simgeleri bağlama etkisini elde etmek için seri koşullu yöntemler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643b7-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="643b7-182">Örneğin, aşağıdaki ikinci yöntem yalnızca her iki yürütecek `A` ve `B` tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="643b7-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="643b7-183">Koşullu öznitelik sınıfları ile kullanma</span><span class="sxs-lookup"><span data-stu-id="643b7-183">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="643b7-184">`Conditional` Özniteliği için öznitelik sınıf tanımını da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="643b7-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="643b7-185">Bu örnekte, özel öznitelik `Documentation` hata ayıklama tanımlanmışsa, yalnızca bilgi meta verileri ekler.</span><span class="sxs-lookup"><span data-stu-id="643b7-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
##  <span data-ttu-id="643b7-186"><a name="CallerInfo"></a>Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-186"><a name="CallerInfo"></a> Caller Info Attributes</span></span>  
 <span data-ttu-id="643b7-187">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643b7-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="643b7-188">Kaynak kodu dosya yolu, kaynak kodu ve arayan üye adı satır numarasını edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="643b7-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="643b7-189">Üye arayan bilgileri almak için isteğe bağlı parametreler uygulanan öznitelikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="643b7-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="643b7-190">Her isteğe bağlı bir parametre varsayılan bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="643b7-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="643b7-191">Aşağıdaki tabloda tanımlanan arayan bilgileri öznitelikleri listeler <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="643b7-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="643b7-192">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="643b7-192">Attribute</span></span>|<span data-ttu-id="643b7-193">Açıklama</span><span class="sxs-lookup"><span data-stu-id="643b7-193">Description</span></span>|<span data-ttu-id="643b7-194">Tür</span><span class="sxs-lookup"><span data-stu-id="643b7-194">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="643b7-195">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="643b7-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="643b7-196">Derleme zamanında yolu budur.</span><span class="sxs-lookup"><span data-stu-id="643b7-196">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="643b7-197">Satır numarası kaynak dosyasındaki yöntemi adı verilir.</span><span class="sxs-lookup"><span data-stu-id="643b7-197">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="643b7-198">Yöntem adı veya çağıranın özellik adı.</span><span class="sxs-lookup"><span data-stu-id="643b7-198">Method name or property name of the caller.</span></span> <span data-ttu-id="643b7-199">Daha fazla bilgi için bkz: [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="643b7-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="643b7-200">Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz: [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="643b7-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <span data-ttu-id="643b7-201"><a name="VB"></a>Visual Basic öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-201"><a name="VB"></a> Visual Basic Attributes</span></span>  
 <span data-ttu-id="643b7-202">Aşağıdaki tabloda Visual Basic'e özel öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="643b7-202">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="643b7-203">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="643b7-203">Attribute</span></span>|<span data-ttu-id="643b7-204">Amaç</span><span class="sxs-lookup"><span data-stu-id="643b7-204">Purpose</span></span>|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="643b7-205">Derleyiciye sınıfı bir COM nesnesi olarak açık olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="643b7-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="643b7-206">Modül üyelerinin modülü için gerekli nitelik kullanarak erişilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="643b7-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="643b7-207">Giriş ve çıkış dosyası ile kullanmak için bir yapı sabit uzunlukta bir dize boyutunu belirtir işlevleri.</span><span class="sxs-lookup"><span data-stu-id="643b7-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="643b7-208">Giriş ve çıkış dosyası ile kullanmak için bir yapı sabit bir dizi boyutunu belirtir işlevleri.</span><span class="sxs-lookup"><span data-stu-id="643b7-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="643b7-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="643b7-209">COMClassAttribute</span></span>  
 <span data-ttu-id="643b7-210">Kullanım `COMClassAttribute` Visual Basic'den COM bileşenleri oluşturma işlemini basitleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="643b7-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="643b7-211">COM nesneleri .NET Framework derlemeleri olmadan ve önemli ölçüde farklı `COMClassAttribute`, çeşitli Visual Basic'den COM nesnesi oluşturmak için adımları izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="643b7-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="643b7-212">Sınıflar ile işaretlenen için `COMClassAttribute`, derleyici bu adımların otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="643b7-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="643b7-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="643b7-213">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="643b7-214">Kullanım `HideModuleNameAttribute` modülü üyeleri yalnızca modülü için gerekli nitelik kullanarak erişilmesine izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="643b7-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="643b7-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="643b7-215">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="643b7-216">Kullanım `VBFixedStringAttribute` sabit uzunlukta bir dize oluşturmak için Visual Basic zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="643b7-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="643b7-217">Varsayılan olarak değişken uzunlukta dizelerdir ve bu öznitelik dosyaları dizelere depolarken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="643b7-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="643b7-218">Aşağıdaki kod bu gösterir:</span><span class="sxs-lookup"><span data-stu-id="643b7-218">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="643b7-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="643b7-219">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="643b7-220">Kullanım `VBFixedArrayAttribute` sabit boyutludur diziler bildirme.</span><span class="sxs-lookup"><span data-stu-id="643b7-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="643b7-221">Visual Basic dizeleri gibi varsayılan değişken uzunlukta diziler değildir.</span><span class="sxs-lookup"><span data-stu-id="643b7-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="643b7-222">Bu öznitelik serileştirmek veya veri dosyaları yazılıyor yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="643b7-222">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643b7-223">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="643b7-223">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="643b7-224">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="643b7-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="643b7-225">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="643b7-225">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="643b7-226">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="643b7-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="643b7-227">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="643b7-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
