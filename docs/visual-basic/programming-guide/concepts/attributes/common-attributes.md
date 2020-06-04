---
title: Ortak Öznitelikler
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 57ef8f103d64a51d896f46d2889d78ec99ff3223
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400725"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="3e6f9-102">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e6f9-102">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="3e6f9-103">Bu konuda Visual Basic programlarında en yaygın olarak kullanılan öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="3e6f9-104">Genel öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e6f9-104">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="3e6f9-105">Kullanımdan kaldırılmış öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-105">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="3e6f9-106">Koşullu öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-106">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="3e6f9-107">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3e6f9-107">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="3e6f9-108">Visual Basic öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3e6f9-108">Visual Basic Attributes</span></span>](#VB)

## <a name="global-attributes"></a><a name="Global"></a><span data-ttu-id="3e6f9-109">Genel öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e6f9-109">Global Attributes</span></span>

<span data-ttu-id="3e6f9-110">Çoğu öznitelik sınıflar veya yöntemler gibi belirli dil öğelerine uygulanır; Ancak, bazı öznitelikler geneldir, tüm derleme veya modül için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="3e6f9-111">Örneğin, özniteliği aşağıdaki <xref:System.Reflection.AssemblyVersionAttribute> gibi bir derlemeye sürüm bilgisi eklemek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="3e6f9-112">Genel öznitelikler, herhangi bir üst düzey `Imports` deyimden sonra ve herhangi bir tür, modül veya ad alanı bildirimlerinden sonra kaynak kodunda görünür.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="3e6f9-113">Genel öznitelikler birden çok kaynak dosyasında görünebilir, ancak dosyaların tek bir derleme geçişinde derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="3e6f9-114">Visual Basic projeler için genel öznitelikler genellikle AssemblyInfo. vb dosyasına konur (Visual Studio 'da bir proje oluşturduğunuzda dosya otomatik olarak oluşturulur).</span><span class="sxs-lookup"><span data-stu-id="3e6f9-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="3e6f9-115">Derleme öznitelikleri, bir derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="3e6f9-116">Bunlar aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-116">They fall into the following categories:</span></span>

- <span data-ttu-id="3e6f9-117">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3e6f9-117">Assembly identity attributes</span></span>

- <span data-ttu-id="3e6f9-118">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e6f9-118">Informational attributes</span></span>

- <span data-ttu-id="3e6f9-119">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3e6f9-119">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="3e6f9-120">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3e6f9-120">Assembly Identity Attributes</span></span>

<span data-ttu-id="3e6f9-121">Üç öznitelik (varsa, güçlü bir ad varsa) bir derlemenin kimliğini belirleme: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="3e6f9-122">Bu öznitelikler, derlemenin tam adını oluşturur ve kodda başvuru yaptığınızda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="3e6f9-123">Öznitelikleri kullanarak bir derlemenin sürümünü ve kültürünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="3e6f9-124">Bununla birlikte, ad değeri derleyici tarafından, derleme [bilgileri Iletişim kutusunda](/visualstudio/ide/reference/assembly-information-dialog-box)VISUAL Studio IDE veya derleme oluşturulduğunda derleme Bağlayıcısı (al. exe) tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="3e6f9-125"><xref:System.Reflection.AssemblyFlagsAttribute>Özniteliği, derlemenin birden çok kopyasının birlikte kullanılıp kullanılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="3e6f9-126">Aşağıdaki tabloda kimlik öznitelikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-126">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="3e6f9-127">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-127">Attribute</span></span>|<span data-ttu-id="3e6f9-128">Amaç</span><span class="sxs-lookup"><span data-stu-id="3e6f9-128">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="3e6f9-129">Bir derlemenin kimliğini tam olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-129">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="3e6f9-130">Bir derlemenin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-130">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="3e6f9-131">Derlemenin desteklediği kültürü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-131">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="3e6f9-132">Bir derlemenin aynı bilgisayarda, aynı işlemde veya aynı uygulama etki alanında yan yana yürütmeyi destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="3e6f9-133">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e6f9-133">Informational Attributes</span></span>

<span data-ttu-id="3e6f9-134">Bir derlemeye ek şirket veya ürün bilgileri sağlamak için bilgilendirici öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="3e6f9-135">Aşağıdaki tabloda, ad alanında tanımlanan bilgilendirici öznitelikler gösterilmektedir <xref:System.Reflection?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3e6f9-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="3e6f9-136">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-136">Attribute</span></span>|<span data-ttu-id="3e6f9-137">Amaç</span><span class="sxs-lookup"><span data-stu-id="3e6f9-137">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="3e6f9-138">Bir derleme bildirimi için bir ürün adı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="3e6f9-139">Bir derleme bildirimi için ticari marka belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="3e6f9-140">Bir derleme bildirimi için bilgilendirici bir sürüm belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="3e6f9-141">Bir derleme bildirimi için bir şirket adı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="3e6f9-142">Bir derleme bildirimi için bir telif hakkı belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="3e6f9-143">Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm numarası kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="3e6f9-144">Derlemenin ortak dil belirtimi (CLS) ile uyumlu olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="3e6f9-145">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3e6f9-145">Assembly Manifest Attributes</span></span>

<span data-ttu-id="3e6f9-146">Derleme bildiriminde bilgi sağlamak için bütünleştirilmiş kod bildirim özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="3e6f9-147">Buna Başlık, açıklama, varsayılan diğer ad ve yapılandırma dahildir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="3e6f9-148">Aşağıdaki tabloda, ad alanında tanımlanan derleme bildirimi öznitelikleri gösterilmektedir <xref:System.Reflection?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3e6f9-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="3e6f9-149">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-149">Attribute</span></span>|<span data-ttu-id="3e6f9-150">Amaç</span><span class="sxs-lookup"><span data-stu-id="3e6f9-150">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="3e6f9-151">Bir derleme bildirimi için derleme başlığını belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="3e6f9-152">Bir derleme bildirimi için derleme açıklamasını belirten özel bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="3e6f9-153">Derleme bildirimi için bir derleme yapılandırması (perakende veya hata ayıklama) belirten özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="3e6f9-154">Bir derleme bildirimi için kolay bir varsayılan diğer ad tanımlar</span><span class="sxs-lookup"><span data-stu-id="3e6f9-154">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="obsolete-attribute"></a><a name="Obsolete"></a><span data-ttu-id="3e6f9-155">Kullanımdan kaldırılmış öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-155">Obsolete Attribute</span></span>

<span data-ttu-id="3e6f9-156">`Obsolete`Özniteliği, bir program varlığını artık kullanım için önerilmeyen bir şekilde işaretler.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="3e6f9-157">Kullanımdan kalktı olarak işaretlenen bir varlığın her kullanımı, özniteliğin nasıl yapılandırıldığına bağlı olarak bir uyarı veya hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="3e6f9-158">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-158">For example:</span></span>

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

<span data-ttu-id="3e6f9-159">Bu örnekte, `Obsolete` özniteliği sınıfa `A` ve yöntemine uygulanır `B.OldMethod` .</span><span class="sxs-lookup"><span data-stu-id="3e6f9-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="3e6f9-160">Öğesine uygulanan öznitelik oluşturucusunun ikinci bağımsız değişkeni `B.OldMethod` olarak ayarlandığından `true` , bu yöntem bir derleyici hatasına neden olur, ancak sınıf kullanımı `A` yalnızca bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="3e6f9-161">Ancak çağırma, `B.NewMethod` hiçbir uyarı veya hata üretir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="3e6f9-162">Öznitelik oluşturucusuna ilk bağımsız değişken olarak girilen dize, uyarının veya hatanın bir parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="3e6f9-163">Örneğin, önceki tanımlarla birlikte kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="3e6f9-164">Sınıf için iki uyarı `A` oluşturulur: biri sınıf başvurusunun bildirimi ve diğeri sınıf oluşturucusu içindir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="3e6f9-165">`Obsolete`Öznitelik bağımsız değişkenler olmadan kullanılabilir, ancak öğenin neden kullanımdan kalkdığına ve bunun yerine ne tür bir açıklama dahil edilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="3e6f9-166">`Obsolete`Özniteliği tek kullanım özniteliğidir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="3e6f9-167">`Obsolete`, için bir diğer addır <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3e6f9-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="conditional-attribute"></a><a name="Conditional"></a><span data-ttu-id="3e6f9-168">Koşullu öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-168">Conditional Attribute</span></span>

<span data-ttu-id="3e6f9-169">`Conditional`Özniteliği bir işlem ön işleme tanımlayıcısına bağımlı bir yöntemin yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="3e6f9-170">`Conditional`Özniteliği için bir diğer addır <xref:System.Diagnostics.ConditionalAttribute> ve bir yönteme veya öznitelik sınıfına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="3e6f9-171">Bu örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı bırakmak için bir yönteme uygulanır:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

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

<span data-ttu-id="3e6f9-172">`TRACE_ON`Tanımlayıcı tanımlanmamışsa, hiçbir izleme çıkışı gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="3e6f9-173">`Conditional`Öznitelik, genellikle `DEBUG` hata ayıklama derlemeleri için izleme ve günlüğe kaydetme özelliklerini etkinleştirmek için tanımlayıcı ile birlikte kullanılır, ancak bunun gibi sürüm yapılarında desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="3e6f9-174">Koşullu olarak işaretlenen bir yöntem çağrıldığında, belirtilen ön işleme simgesinin varlığı veya yokluğu, çağrının eklenip eklenmeyeceğini veya atlanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="3e6f9-175">Sembol tanımlanmışsa, çağrı dahil edilir; Aksi takdirde, çağrı atlanır.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="3e6f9-176">Kullanılarak, `Conditional` blokların içindeki yöntemlerin içine yerleştirilmesi için aşağıdaki gibi bir temizleyici, daha zarif ve daha az hataya açık bir alternatiftir `#if…#endif` :</span><span class="sxs-lookup"><span data-stu-id="3e6f9-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="3e6f9-177">Koşullu Yöntem bir sınıf veya yapı bildiriminde bir yöntem olmalıdır ve dönüş değeri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="3e6f9-178">Birden çok tanımlayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="3e6f9-178">Using Multiple Identifiers</span></span>

<span data-ttu-id="3e6f9-179">Bir yöntemin birden çok `Conditional` özniteliği varsa, koşullu simgelerden en az biri tanımlanmışsa yöntemine bir çağrı dahil edilir (başka bir deyişle, semboller or işleci kullanılarak mantıksal olarak birbirlerine bağlanır).</span><span class="sxs-lookup"><span data-stu-id="3e6f9-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="3e6f9-180">Bu örnekte, ya da birinin varlığı `A` `B` bir yöntem çağrısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="3e6f9-181">VE işlecini kullanarak sembolleri mantıksal olarak bağlama etkisini elde etmek için, seri koşullu yöntemleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="3e6f9-182">Örneğin, aşağıdaki ikinci yöntem yalnızca `A` ve `B` tanımlanırsa yürütülür:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

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

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="3e6f9-183">Öznitelik sınıfları ile koşullu kullanma</span><span class="sxs-lookup"><span data-stu-id="3e6f9-183">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="3e6f9-184">`Conditional`Öznitelik, öznitelik sınıfı tanımına da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="3e6f9-185">Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

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

## <a name="caller-info-attributes"></a><a name="CallerInfo"></a><span data-ttu-id="3e6f9-186">Arayan bilgileri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3e6f9-186">Caller Info Attributes</span></span>

<span data-ttu-id="3e6f9-187">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="3e6f9-188">Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="3e6f9-189">Üye çağıran bilgilerini almak için, isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="3e6f9-190">Her isteğe bağlı parametre varsayılan bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="3e6f9-191">Aşağıdaki tabloda, ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="3e6f9-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="3e6f9-192">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-192">Attribute</span></span>|<span data-ttu-id="3e6f9-193">Description</span><span class="sxs-lookup"><span data-stu-id="3e6f9-193">Description</span></span>|<span data-ttu-id="3e6f9-194">Tür</span><span class="sxs-lookup"><span data-stu-id="3e6f9-194">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="3e6f9-195">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="3e6f9-196">Bu, derleme zamanının yoludur.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-196">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="3e6f9-197">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-197">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="3e6f9-198">Çağıranın Yöntem adı veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-198">Method name or property name of the caller.</span></span> <span data-ttu-id="3e6f9-199">Daha fazla bilgi için bkz. [arayan bilgileri (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="3e6f9-199">For more information, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>|`String`|

<span data-ttu-id="3e6f9-200">Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz. [arayan bilgileri (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="3e6f9-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>

## <a name="visual-basic-attributes"></a><a name="VB"></a><span data-ttu-id="3e6f9-201">Visual Basic öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="3e6f9-201">Visual Basic Attributes</span></span>

<span data-ttu-id="3e6f9-202">Aşağıdaki tablo Visual Basic özgü öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-202">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="3e6f9-203">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e6f9-203">Attribute</span></span>|<span data-ttu-id="3e6f9-204">Amaç</span><span class="sxs-lookup"><span data-stu-id="3e6f9-204">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="3e6f9-205">Derleyicinin sınıfın bir COM nesnesi olarak kullanıma sunulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="3e6f9-206">Modül üyelerine yalnızca modül için gereken nitelik kullanılarak erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="3e6f9-207">Dosya girişi ve çıkış işlevleriyle kullanılmak üzere bir yapıda sabit uzunluklu dizenin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="3e6f9-208">Dosya girişi ve çıkış işlevleriyle kullanılmak üzere bir yapıda sabit bir dizinin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="3e6f9-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="3e6f9-209">COMClassAttribute</span></span>

<span data-ttu-id="3e6f9-210">`COMClassAttribute`VISUAL BASIC com bileşenleri oluşturma işlemini basitleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="3e6f9-211">COM nesneleri .NET Framework derlemelerinden oldukça farklıdır ve olmadan `COMClassAttribute` , Visual Basic BIR com nesnesi oluşturmak için birkaç adımı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="3e6f9-212">İle işaretlenen sınıflar için `COMClassAttribute` , derleyici bu adımların çoğunu otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="3e6f9-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="3e6f9-213">HideModuleNameAttribute</span></span>

<span data-ttu-id="3e6f9-214">Modül `HideModuleNameAttribute` üyelerine yalnızca modül için gereken nitelik kullanılarak erişilmesine izin vermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="3e6f9-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="3e6f9-215">VBFixedStringAttribute</span></span>

<span data-ttu-id="3e6f9-216">`VBFixedStringAttribute`Visual Basic sabit uzunluklu bir dize oluşturacak şekilde zorlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="3e6f9-217">Dizeler varsayılan olarak değişken uzunluktadır ve bu öznitelik, dizeleri dosyalara depolarken yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="3e6f9-218">Aşağıdaki kod bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="3e6f9-218">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="3e6f9-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="3e6f9-219">VBFixedArrayAttribute</span></span>

<span data-ttu-id="3e6f9-220">`VBFixedArrayAttribute`Boyut olarak düzeltilen dizileri bildirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="3e6f9-221">Visual Basic dizeleri gibi diziler, varsayılan olarak değişken uzunluktadır.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="3e6f9-222">Bu öznitelik, dosyalara veri serileştirilirken veya verileri yazarken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-222">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e6f9-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e6f9-223">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="3e6f9-224">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3e6f9-224">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="3e6f9-225">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e6f9-225">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="3e6f9-226">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e6f9-226">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="3e6f9-227">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e6f9-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
