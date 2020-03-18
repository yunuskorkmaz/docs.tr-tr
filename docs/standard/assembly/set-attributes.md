---
title: Derleme özniteliklerini ayarlama
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 0e4e2e595ed4f95511bd23ab0ed00139f71b2c8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740479"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="8f3dd-102">Derleme özniteliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="8f3dd-102">Set assembly attributes</span></span>

<span data-ttu-id="8f3dd-103">Derleme öznitelikleri, derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-103">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="8f3dd-104">Öznitelikler aşağıdaki bilgi kümelerine ayrılır:</span><span class="sxs-lookup"><span data-stu-id="8f3dd-104">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="8f3dd-105">Montaj kimlik öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8f3dd-105">Assembly identity attributes</span></span>

- <span data-ttu-id="8f3dd-106">Bilgilendirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="8f3dd-106">Informational attributes</span></span>

- <span data-ttu-id="8f3dd-107">Derleme bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8f3dd-107">Assembly manifest attributes</span></span>

- <span data-ttu-id="8f3dd-108">Güçlü ad öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8f3dd-108">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="8f3dd-109">Montaj kimlik öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8f3dd-109">Assembly identity attributes</span></span>

<span data-ttu-id="8f3dd-110">Güçlü bir adla birlikte (varsa) üç öznitelik, bir derlemenin kimliğini belirler: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-110">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="8f3dd-111">Bu öznitelikler derlemenin tam adını oluşturur ve derlemeyi kodla ifade ederken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-111">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="8f3dd-112">Derlemenin sürümünü ve kültürünü ayarlamak için öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-112">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="8f3dd-113">Derleyici veya [Derleme Bağlayıcısı (Al.exe),](../../framework/tools/al-exe-assembly-linker.md) derleme bildirimini içeren dosyayı temel alınca, derleme oluşturulduğunda ad değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-113">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="8f3dd-114">Aşağıdaki tabloda sürüm ve kültür öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-114">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="8f3dd-115">Derleme kimlik özniteliği</span><span class="sxs-lookup"><span data-stu-id="8f3dd-115">Assembly identity attribute</span></span>|<span data-ttu-id="8f3dd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f3dd-116">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="8f3dd-117">Derlemenin desteklediği kültürü gösteren numaralandırılmış alan.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-117">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="8f3dd-118">Bir derleme, varsayılan kültür için kaynakları içerdiğini belirterek kültür bağımsızlığını da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-118">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="8f3dd-119">**Not:**  Çalışma zamanı, uydu derlemesi olarak null olarak ayarlanmış kültür özniteliği olmayan herhangi bir derlemeyi davranır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-119">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="8f3dd-120">Bu tür derlemeler uydu montaj bağlama kurallarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-120">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="8f3dd-121">Daha fazla bilgi için [çalışma zamanının derlemeleri nasıl bulabildiğini](../../framework/deployment/how-the-runtime-locates-assemblies.md)görün.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-121">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="8f3dd-122">Derlemenin yan yana çalıştırılıp çalıştırılamayacağı gibi derleme özniteliklerini ayarlayan değer.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-122">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="8f3dd-123">Biçim *ana'daki*sayısal değer. *küçük*. *inşa edin.* *revizyon* (örneğin, 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="8f3dd-123">Numeric value in the format *major*.*minor*.*build*.*revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="8f3dd-124">Ortak dil çalışma süresi, bağlı adlandırılmış derlemelerde bağlama işlemleri gerçekleştirmek için bu değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-124">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="8f3dd-125">**Not:**  Öznitelik <xref:System.Reflection.AssemblyInformationalVersionAttribute> bir derlemeye uygulanmazsa, öznitelik <xref:System.Reflection.AssemblyVersionAttribute> tarafından belirtilen sürüm numarası <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> ve özellikleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-125">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="8f3dd-126">Aşağıdaki kod örneği, sürüm ve kültür özniteliklerinin bir derlemeye nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-126">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a><span data-ttu-id="8f3dd-127">Bilgilendirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="8f3dd-127">Informational attributes</span></span>

<span data-ttu-id="8f3dd-128">Bir derleme için ek şirket veya ürün bilgileri sağlamak için bilgi özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-128">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="8f3dd-129">Aşağıdaki tabloda, bir derlemeye uygulayabileceğiniz bilgi öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-129">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="8f3dd-130">Bilgilendirme özniteliği</span><span class="sxs-lookup"><span data-stu-id="8f3dd-130">Informational attribute</span></span>|<span data-ttu-id="8f3dd-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f3dd-131">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="8f3dd-132">Şirket adını belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-132">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="8f3dd-133">Telif hakkı bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-133">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="8f3dd-134">Win32 dosya sürüm numarasını belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-134">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="8f3dd-135">Bu normalde varsayılan olarak derleme sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-135">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="8f3dd-136">Tam ürün sürüm numarası gibi ortak dil çalışma zamanı tarafından kullanılmayan sürüm bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-136">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="8f3dd-137">**Not:**  Bu öznitelik bir derlemeye uygulanırsa, belirttiği dize <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> özelliği kullanılarak çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-137">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8f3dd-138">Dize, yol ve kayıt defteri anahtarında <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-138">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="8f3dd-139">Ürün bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-139">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="8f3dd-140">Ticari marka bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-140">String value specifying trademark information.</span></span>|

<span data-ttu-id="8f3dd-141">Bu öznitelikler derlemenin Windows Properties sayfasında görünebilir veya kendi Win32 kaynak dosyanızı belirtmek için **/win32res** derleyicisi seçeneğini kullanarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-141">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="8f3dd-142">Derleme bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8f3dd-142">Assembly manifest attributes</span></span>

<span data-ttu-id="8f3dd-143">Başlık, açıklama, varsayılan takma ad ve yapılandırma gibi derleme bildiriminde bilgi sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-143">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="8f3dd-144">Aşağıdaki tabloda derleme bildirimi öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-144">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="8f3dd-145">Derleme bildirim özniteliği</span><span class="sxs-lookup"><span data-stu-id="8f3dd-145">Assembly manifest attribute</span></span>|<span data-ttu-id="8f3dd-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f3dd-146">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="8f3dd-147">Perakende veya Hata Ayıklama gibi derlemeyapılandırmasını gösteren dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-147">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="8f3dd-148">Çalışma süresi bu değeri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-148">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="8f3dd-149">Derlemelere başvurarak kullanılacak varsayılan bir diğer adı belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-149">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="8f3dd-150">Bu değer, derlemenin adı uygun olmadığında (GUID değeri gibi) dostça bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-150">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="8f3dd-151">Bu değer, tam montaj adının kısa bir biçimi olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-151">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="8f3dd-152">Derlemenin niteliğini ve amacını özetleyen kısa bir açıklama belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-152">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="8f3dd-153">Montaj için uygun bir ad belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-153">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="8f3dd-154">Örneğin, *comdlg* adlı bir derleme microsoft ortak iletişim denetimi başlığına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-154">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="8f3dd-155">Güçlü ad öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8f3dd-155">Strong name attributes</span></span>

<span data-ttu-id="8f3dd-156">Derleme için güçlü bir ad ayarlamak için güçlü ad öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-156">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="8f3dd-157">Aşağıdaki tabloda güçlü ad öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-157">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="8f3dd-158">Güçlü ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="8f3dd-158">Strong name attribute</span></span>|<span data-ttu-id="8f3dd-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f3dd-159">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="8f3dd-160">Gecikme imzalamanın kullanıldığını belirten boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-160">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="8f3dd-161">Ortak anahtarı (gecikme imzalamayı kullanıyorsanız) veya bu özniteliğin oluşturucuya parametre olarak aktarılan ortak ve özel anahtarları içeren dosyanın adını gösteren dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-161">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="8f3dd-162">Dosya adının kaynak dosya yolu ile değil, çıktı dosyası yoluna *(.exe* veya *.dll)* göreli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-162">Note that the file name is relative to the output file path (the *.exe* or *.dll*), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="8f3dd-163">Bu özniteliğin oluşturucuya parametre olarak geçirilen anahtar çiftini içeren anahtar kapsayıcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-163">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="8f3dd-164">Aşağıdaki kod örneği, *myKey.snk*adlı ortak anahtar dosyası içeren güçlü bir anahtar dosyası oluşturmak için gecikme imzalamayı kullanırken uygulanacak öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-164">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk*.</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a><span data-ttu-id="8f3dd-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f3dd-165">See also</span></span>

- [<span data-ttu-id="8f3dd-166">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f3dd-166">Create assemblies</span></span>](create.md)
