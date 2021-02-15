---
description: 'Daha fazla bilgi edinin: ortak öznitelikler (Visual Basic)'
title: Ortak Öznitelikler
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 875554b69a23640c2d67367c93b56c34c286df37
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437793"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="c7f85-103">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7f85-103">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="c7f85-104">Bu konuda Visual Basic programlarında en yaygın olarak kullanılan öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7f85-104">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="c7f85-105">Genel öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7f85-105">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="c7f85-106">Kullanımdan kaldırılmış öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-106">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="c7f85-107">Koşullu öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-107">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="c7f85-108">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7f85-108">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="c7f85-109">Visual Basic öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7f85-109">Visual Basic Attributes</span></span>](#VB)

## <a name="global-attributes"></a><a name="Global"></a> <span data-ttu-id="c7f85-110">Genel öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7f85-110">Global Attributes</span></span>

<span data-ttu-id="c7f85-111">Çoğu öznitelik sınıflar veya yöntemler gibi belirli dil öğelerine uygulanır; Ancak, bazı öznitelikler geneldir, tüm derleme veya modül için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-111">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="c7f85-112">Örneğin, özniteliği aşağıdaki <xref:System.Reflection.AssemblyVersionAttribute> gibi bir derlemeye sürüm bilgisi eklemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c7f85-112">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="c7f85-113">Genel öznitelikler, herhangi bir üst düzey `Imports` deyimden sonra ve herhangi bir tür, modül veya ad alanı bildirimlerinden sonra kaynak kodunda görünür.</span><span class="sxs-lookup"><span data-stu-id="c7f85-113">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="c7f85-114">Genel öznitelikler birden çok kaynak dosyasında görünebilir, ancak dosyaların tek bir derleme geçişinde derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-114">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="c7f85-115">Visual Basic projeler için genel öznitelikler genellikle AssemblyInfo. vb dosyasına konur (Visual Studio 'da bir proje oluşturduğunuzda dosya otomatik olarak oluşturulur).</span><span class="sxs-lookup"><span data-stu-id="c7f85-115">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="c7f85-116">Derleme öznitelikleri, bir derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-116">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="c7f85-117">Bunlar aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="c7f85-117">They fall into the following categories:</span></span>

- <span data-ttu-id="c7f85-118">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7f85-118">Assembly identity attributes</span></span>

- <span data-ttu-id="c7f85-119">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7f85-119">Informational attributes</span></span>

- <span data-ttu-id="c7f85-120">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7f85-120">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="c7f85-121">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7f85-121">Assembly Identity Attributes</span></span>

<span data-ttu-id="c7f85-122">Üç öznitelik (varsa, güçlü bir ad varsa) bir derlemenin kimliğini belirleme: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="c7f85-122">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="c7f85-123">Bu öznitelikler, derlemenin tam adını oluşturur ve kodda başvuru yaptığınızda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-123">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="c7f85-124">Öznitelikleri kullanarak bir derlemenin sürümünü ve kültürünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f85-124">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="c7f85-125">Bununla birlikte, ad değeri derleyici tarafından, derleme [bilgileri Iletişim kutusunda](/visualstudio/ide/reference/assembly-information-dialog-box)VISUAL Studio IDE veya bütünleştirilmiş kod bildirimini içeren dosya temelinde derleme bağlayıcı (Al.exe) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c7f85-125">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="c7f85-126"><xref:System.Reflection.AssemblyFlagsAttribute>Özniteliği, derlemenin birden çok kopyasının birlikte kullanılıp kullanılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-126">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="c7f85-127">Aşağıdaki tabloda kimlik öznitelikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-127">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="c7f85-128">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-128">Attribute</span></span>|<span data-ttu-id="c7f85-129">Amaç</span><span class="sxs-lookup"><span data-stu-id="c7f85-129">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="c7f85-130">Bir derlemenin kimliğini tam olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-130">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="c7f85-131">Bir derlemenin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-131">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="c7f85-132">Derlemenin desteklediği kültürü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-132">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="c7f85-133">Bir derlemenin aynı bilgisayarda, aynı işlemde veya aynı uygulama etki alanında yan yana yürütmeyi destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-133">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="c7f85-134">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7f85-134">Informational Attributes</span></span>

<span data-ttu-id="c7f85-135">Bir derlemeye ek şirket veya ürün bilgileri sağlamak için bilgilendirici öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f85-135">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="c7f85-136">Aşağıdaki tabloda, ad alanında tanımlanan bilgilendirici öznitelikler gösterilmektedir <xref:System.Reflection?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c7f85-136">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="c7f85-137">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-137">Attribute</span></span>|<span data-ttu-id="c7f85-138">Amaç</span><span class="sxs-lookup"><span data-stu-id="c7f85-138">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="c7f85-139">Bir derleme bildirimi için bir ürün adı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-139">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="c7f85-140">Bir derleme bildirimi için ticari marka belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-140">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="c7f85-141">Bir derleme bildirimi için bilgilendirici bir sürüm belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-141">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="c7f85-142">Bir derleme bildirimi için bir şirket adı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-142">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="c7f85-143">Bir derleme bildirimi için bir telif hakkı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-143">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="c7f85-144">Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm numarası kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="c7f85-144">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="c7f85-145">Derlemenin ortak dil belirtimi (CLS) ile uyumlu olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-145">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="c7f85-146">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7f85-146">Assembly Manifest Attributes</span></span>

<span data-ttu-id="c7f85-147">Derleme bildiriminde bilgi sağlamak için bütünleştirilmiş kod bildirim özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f85-147">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="c7f85-148">Buna Başlık, açıklama, varsayılan diğer ad ve yapılandırma dahildir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-148">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="c7f85-149">Aşağıdaki tabloda, ad alanında tanımlanan derleme bildirimi öznitelikleri gösterilmektedir <xref:System.Reflection?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c7f85-149">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="c7f85-150">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-150">Attribute</span></span>|<span data-ttu-id="c7f85-151">Amaç</span><span class="sxs-lookup"><span data-stu-id="c7f85-151">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="c7f85-152">Bir derleme bildirimi için derleme başlığını belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-152">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="c7f85-153">Bir derleme bildirimi için derleme açıklamasını belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-153">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="c7f85-154">Derleme bildirimi için bir derleme yapılandırması (perakende veya hata ayıklama) belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-154">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="c7f85-155">Bir derleme bildirimi için kolay bir varsayılan diğer ad tanımlar</span><span class="sxs-lookup"><span data-stu-id="c7f85-155">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="obsolete-attribute"></a><a name="Obsolete"></a> <span data-ttu-id="c7f85-156">Kullanımdan kaldırılmış öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-156">Obsolete Attribute</span></span>

<span data-ttu-id="c7f85-157">`Obsolete`Özniteliği, bir program varlığını artık kullanım için önerilmeyen bir şekilde işaretler.</span><span class="sxs-lookup"><span data-stu-id="c7f85-157">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="c7f85-158">Kullanımdan kalktı olarak işaretlenen bir varlığın her kullanımı, özniteliğin nasıl yapılandırıldığına bağlı olarak bir uyarı veya hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7f85-158">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="c7f85-159">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c7f85-159">For example:</span></span>

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

<span data-ttu-id="c7f85-160">Bu örnekte, `Obsolete` özniteliği sınıfa `A` ve yöntemine uygulanır `B.OldMethod` .</span><span class="sxs-lookup"><span data-stu-id="c7f85-160">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="c7f85-161">Öğesine uygulanan öznitelik oluşturucusunun ikinci bağımsız değişkeni `B.OldMethod` olarak ayarlandığından `true` , bu yöntem bir derleyici hatasına neden olur, ancak sınıf kullanımı `A` yalnızca bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7f85-161">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="c7f85-162">Ancak çağırma, `B.NewMethod` hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-162">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="c7f85-163">Öznitelik oluşturucusuna ilk bağımsız değişken olarak girilen dize, uyarının veya hatanın bir parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-163">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="c7f85-164">Örneğin, önceki tanımlarla birlikte kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c7f85-164">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="c7f85-165">Sınıf için iki uyarı `A` oluşturulur: biri sınıf başvurusunun bildirimi ve diğeri sınıf oluşturucusu içindir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-165">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="c7f85-166">`Obsolete`Öznitelik bağımsız değişkenler olmadan kullanılabilir, ancak öğenin neden kullanımdan kalkdığına ve bunun yerine ne tür bir açıklama dahil edilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-166">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="c7f85-167">`Obsolete`Özniteliği tek kullanım özniteliğidir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-167">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="c7f85-168">`Obsolete` , için bir diğer addır <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c7f85-168">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="conditional-attribute"></a><a name="Conditional"></a> <span data-ttu-id="c7f85-169">Koşullu öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-169">Conditional Attribute</span></span>

<span data-ttu-id="c7f85-170">`Conditional`Özniteliği bir işlem ön işleme tanımlayıcısına bağımlı bir yöntemin yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7f85-170">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="c7f85-171">`Conditional`Özniteliği için bir diğer addır <xref:System.Diagnostics.ConditionalAttribute> ve bir yönteme veya öznitelik sınıfına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-171">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="c7f85-172">Bu örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı bırakmak için bir yönteme uygulanır:</span><span class="sxs-lookup"><span data-stu-id="c7f85-172">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

```vb
#Const TRACE_ON = True
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

<span data-ttu-id="c7f85-173">`TRACE_ON`Tanımlayıcı tanımlanmamışsa, hiçbir izleme çıkışı gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="c7f85-173">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="c7f85-174">`Conditional`Öznitelik, genellikle `DEBUG` hata ayıklama derlemeleri için izleme ve günlüğe kaydetme özelliklerini etkinleştirmek için tanımlayıcı ile birlikte kullanılır, ancak bunun gibi sürüm yapılarında desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="c7f85-174">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="c7f85-175">Koşullu olarak işaretlenen bir yöntem çağrıldığında, belirtilen ön işleme simgesinin varlığı veya yokluğu, çağrının eklenip eklenmeyeceğini veya atlanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c7f85-175">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="c7f85-176">Sembol tanımlanmışsa, çağrı dahil edilir; Aksi takdirde, çağrı atlanır.</span><span class="sxs-lookup"><span data-stu-id="c7f85-176">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="c7f85-177">Kullanılarak, `Conditional` blokların içindeki yöntemlerin içine yerleştirilmesi için aşağıdaki gibi bir temizleyici, daha zarif ve daha az hataya açık bir alternatiftir `#if…#endif` :</span><span class="sxs-lookup"><span data-stu-id="c7f85-177">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="c7f85-178">Koşullu Yöntem bir sınıf veya yapı bildiriminde bir yöntem olmalıdır ve dönüş değeri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-178">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="c7f85-179">Birden çok tanımlayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="c7f85-179">Using Multiple Identifiers</span></span>

<span data-ttu-id="c7f85-180">Bir yöntemin birden çok `Conditional` özniteliği varsa, koşullu simgelerden en az biri tanımlanmışsa yöntemine bir çağrı dahil edilir (başka bir deyişle, semboller or işleci kullanılarak mantıksal olarak birbirlerine bağlanır).</span><span class="sxs-lookup"><span data-stu-id="c7f85-180">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="c7f85-181">Bu örnekte, ya da birinin varlığı `A` `B` bir yöntem çağrısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="c7f85-181">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="c7f85-182">VE işlecini kullanarak sembolleri mantıksal olarak bağlama etkisini elde etmek için, seri koşullu yöntemleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f85-182">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="c7f85-183">Örneğin, aşağıdaki ikinci yöntem yalnızca `A` ve `B` tanımlanırsa yürütülür:</span><span class="sxs-lookup"><span data-stu-id="c7f85-183">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

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

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="c7f85-184">Öznitelik sınıfları ile koşullu kullanma</span><span class="sxs-lookup"><span data-stu-id="c7f85-184">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="c7f85-185">`Conditional`Öznitelik, öznitelik sınıfı tanımına da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-185">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="c7f85-186">Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="c7f85-186">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

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

## <a name="caller-info-attributes"></a><a name="CallerInfo"></a> <span data-ttu-id="c7f85-187">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7f85-187">Caller Info Attributes</span></span>

<span data-ttu-id="c7f85-188">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f85-188">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="c7f85-189">Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f85-189">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="c7f85-190">Üye çağıran bilgilerini almak için, isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c7f85-190">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="c7f85-191">Her isteğe bağlı parametre varsayılan bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-191">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="c7f85-192">Aşağıdaki tabloda, ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="c7f85-192">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="c7f85-193">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-193">Attribute</span></span>|<span data-ttu-id="c7f85-194">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7f85-194">Description</span></span>|<span data-ttu-id="c7f85-195">Tür</span><span class="sxs-lookup"><span data-stu-id="c7f85-195">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="c7f85-196">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="c7f85-196">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="c7f85-197">Bu, derleme zamanının yoludur.</span><span class="sxs-lookup"><span data-stu-id="c7f85-197">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="c7f85-198">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="c7f85-198">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="c7f85-199">Çağıranın Yöntem adı veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="c7f85-199">Method name or property name of the caller.</span></span> <span data-ttu-id="c7f85-200">Daha fazla bilgi için bkz. [arayan bilgileri (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="c7f85-200">For more information, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>|`String`|

<span data-ttu-id="c7f85-201">Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz. [arayan bilgileri (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="c7f85-201">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>

## <a name="visual-basic-attributes"></a><a name="VB"></a> <span data-ttu-id="c7f85-202">Visual Basic öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7f85-202">Visual Basic Attributes</span></span>

<span data-ttu-id="c7f85-203">Aşağıdaki tablo Visual Basic özgü öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c7f85-203">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="c7f85-204">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7f85-204">Attribute</span></span>|<span data-ttu-id="c7f85-205">Amaç</span><span class="sxs-lookup"><span data-stu-id="c7f85-205">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="c7f85-206">Derleyicinin sınıfın bir COM nesnesi olarak kullanıma sunulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-206">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="c7f85-207">Modül üyelerine yalnızca modül için gereken nitelik kullanılarak erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-207">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="c7f85-208">Dosya girişi ve çıkış işlevleriyle kullanılmak üzere bir yapıda sabit uzunluklu dizenin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-208">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="c7f85-209">Dosya girişi ve çıkış işlevleriyle kullanılmak üzere bir yapıda sabit bir dizinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-209">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="c7f85-210">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="c7f85-210">COMClassAttribute</span></span>

<span data-ttu-id="c7f85-211">`COMClassAttribute`VISUAL BASIC com bileşenleri oluşturma işlemini basitleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7f85-211">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="c7f85-212">COM nesneleri .NET Framework derlemelerinden oldukça farklıdır ve olmadan `COMClassAttribute` , Visual Basic BIR com nesnesi oluşturmak için birkaç adımı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-212">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="c7f85-213">İle işaretlenen sınıflar için `COMClassAttribute` , derleyici bu adımların çoğunu otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7f85-213">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="c7f85-214">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="c7f85-214">HideModuleNameAttribute</span></span>

<span data-ttu-id="c7f85-215">Modül `HideModuleNameAttribute` üyelerine yalnızca modül için gereken nitelik kullanılarak erişilmesine izin vermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7f85-215">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="c7f85-216">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="c7f85-216">VBFixedStringAttribute</span></span>

<span data-ttu-id="c7f85-217">`VBFixedStringAttribute`Visual Basic sabit uzunluklu bir dize oluşturacak şekilde zorlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7f85-217">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="c7f85-218">Dizeler varsayılan olarak değişken uzunluktadır ve bu öznitelik, dizeleri dosyalara depolarken yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="c7f85-218">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="c7f85-219">Aşağıdaki kod bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="c7f85-219">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="c7f85-220">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="c7f85-220">VBFixedArrayAttribute</span></span>

<span data-ttu-id="c7f85-221">`VBFixedArrayAttribute`Boyut olarak düzeltilen dizileri bildirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7f85-221">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="c7f85-222">Visual Basic dizeleri gibi diziler, varsayılan olarak değişken uzunluktadır.</span><span class="sxs-lookup"><span data-stu-id="c7f85-222">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="c7f85-223">Bu öznitelik, dosyalara veri serileştirilirken veya verileri yazarken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7f85-223">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7f85-224">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7f85-224">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="c7f85-225">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7f85-225">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="c7f85-226">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7f85-226">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="c7f85-227">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7f85-227">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="c7f85-228">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7f85-228">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
