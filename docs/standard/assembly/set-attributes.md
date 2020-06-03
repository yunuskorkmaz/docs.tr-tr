---
title: Derleme özniteliklerini ayarlama
description: Derleme kimliği, bilgilendirme, derleme bildirimi ve tanımlayıcı ad öznitelikleri dahil olmak üzere .NET derlemesi için derleme öznitelikleri ayarlayabilirsiniz.
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
ms.openlocfilehash: e3a077dcd1b62a4676a3ac6492a90e38c548e41b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378642"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="8ca1a-103">Derleme özniteliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ca1a-103">Set assembly attributes</span></span>

<span data-ttu-id="8ca1a-104">Derleme öznitelikleri, bir derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-104">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="8ca1a-105">Öznitelikler aşağıdaki bilgi kümelerine ayrılır:</span><span class="sxs-lookup"><span data-stu-id="8ca1a-105">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="8ca1a-106">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8ca1a-106">Assembly identity attributes</span></span>

- <span data-ttu-id="8ca1a-107">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ca1a-107">Informational attributes</span></span>

- <span data-ttu-id="8ca1a-108">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8ca1a-108">Assembly manifest attributes</span></span>

- <span data-ttu-id="8ca1a-109">Tanımlayıcı ad öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8ca1a-109">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="8ca1a-110">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8ca1a-110">Assembly identity attributes</span></span>

<span data-ttu-id="8ca1a-111">Bir tanımlayıcı ad (varsa) ile birlikte üç öznitelik, bir derlemenin kimliğini belirleme: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-111">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="8ca1a-112">Bu öznitelikler, derlemenin tam adını oluşturur ve koddaki derlemeye başvurulduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-112">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="8ca1a-113">Öznitelikleri, bir derlemenin sürümünü ve kültürünü ayarlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-113">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="8ca1a-114">Derleyici veya [derleme Bağlayıcısı (al. exe)](../../framework/tools/al-exe-assembly-linker.md) , derleme bildirimini içeren dosyaya bağlı olarak, derleme oluşturulduğunda ad değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-114">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="8ca1a-115">Aşağıdaki tabloda sürüm ve kültür öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-115">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="8ca1a-116">Bütünleştirilmiş kod kimliği özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ca1a-116">Assembly identity attribute</span></span>|<span data-ttu-id="8ca1a-117">Description</span><span class="sxs-lookup"><span data-stu-id="8ca1a-117">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="8ca1a-118">Derlemenin desteklediği kültürü gösteren numaralandırılmış alan.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-118">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="8ca1a-119">Bir bütünleştirilmiş kod ayrıca kültür bağımsızlığını belirtebilir ve bu, varsayılan kültürün kaynaklarını içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-119">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="8ca1a-120">**Note:**  Çalışma zamanı, kültür özniteliği olmayan herhangi bir derlemeyi uydu derlemesi olarak null olarak ayarlanmış şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-120">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="8ca1a-121">Bu tür derlemeler uydu derleme bağlama kurallarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-121">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="8ca1a-122">Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="8ca1a-122">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="8ca1a-123">Derlemenin yan yana çalıştırılıp çalıştırılmayacağı gibi, derleme özniteliklerini ayarlayan değer.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-123">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="8ca1a-124">*Birincil*biçimdeki sayısal değer. *küçük*. *oluşturun*. *Düzeltme* (örneğin, 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="8ca1a-124">Numeric value in the format *major*.*minor*.*build*.*revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="8ca1a-125">Ortak dil çalışma zamanı, tanımlayıcı adlı derlemelerde bağlama işlemleri gerçekleştirmek için bu değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-125">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="8ca1a-126">**Note:**  <xref:System.Reflection.AssemblyInformationalVersionAttribute>Özniteliği bir derlemeye uygulanmadığından, özniteliği tarafından belirtilen sürüm numarası <xref:System.Reflection.AssemblyVersionAttribute> <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> , <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> , ve özellikleri tarafından kullanılır <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8ca1a-126">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="8ca1a-127">Aşağıdaki kod örneği, bir derlemeye sürüm ve kültür özniteliklerinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-127">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

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

## <a name="informational-attributes"></a><span data-ttu-id="8ca1a-128">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ca1a-128">Informational attributes</span></span>

<span data-ttu-id="8ca1a-129">Bir derlemeye ek şirket veya ürün bilgileri sağlamak için bilgilendirici öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-129">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="8ca1a-130">Aşağıdaki tabloda, bir derlemeye uygulayabileceğiniz bilgilendirici öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-130">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="8ca1a-131">Bilgilendirici özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ca1a-131">Informational attribute</span></span>|<span data-ttu-id="8ca1a-132">Description</span><span class="sxs-lookup"><span data-stu-id="8ca1a-132">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="8ca1a-133">Şirket adını belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-133">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="8ca1a-134">Telif hakkı bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-134">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="8ca1a-135">Win32 dosya sürümü numarasını belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-135">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="8ca1a-136">Bu, normalde derleme sürümünü varsayılan olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-136">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="8ca1a-137">Tam ürün sürümü numarası gibi ortak dil çalışma zamanı tarafından kullanılmayan sürüm bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-137">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="8ca1a-138">**Note:**  Bu öznitelik bir derlemeye uygulanırsa, belirttiği dize özelliği kullanılarak çalışma zamanında elde edilebilir <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8ca1a-138">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8ca1a-139">Dize, ve özellikleri tarafından sunulan yol ve kayıt defteri anahtarında de kullanılır <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8ca1a-139">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="8ca1a-140">Ürün bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-140">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="8ca1a-141">Ticari marka bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-141">String value specifying trademark information.</span></span>|

<span data-ttu-id="8ca1a-142">Bu öznitelikler, derlemenin Windows özellikleri sayfasında görünebilir veya kendi Win32 kaynak dosyanızı belirtmek için **/win32res** derleyici seçeneği kullanılarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-142">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="8ca1a-143">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8ca1a-143">Assembly manifest attributes</span></span>

<span data-ttu-id="8ca1a-144">Derleme bildiriminde başlık, açıklama, varsayılan diğer ad ve yapılandırma dahil olmak üzere bilgi sağlamak için bütünleştirilmiş kod bildirim özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-144">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="8ca1a-145">Aşağıdaki tabloda, derleme bildirim öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-145">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="8ca1a-146">Bütünleştirilmiş kod bildirim özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ca1a-146">Assembly manifest attribute</span></span>|<span data-ttu-id="8ca1a-147">Description</span><span class="sxs-lookup"><span data-stu-id="8ca1a-147">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="8ca1a-148">Derlemenin, perakende veya hata ayıklama gibi yapılandırmasını gösteren dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-148">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="8ca1a-149">Çalışma zamanı bu değeri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-149">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="8ca1a-150">Başvurulan derlemelere göre kullanılacak varsayılan bir diğer ad belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-150">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="8ca1a-151">Bu değer, derlemenin kendisinin adı kolay değil (bir GUID değeri gibi) kolay bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-151">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="8ca1a-152">Bu değer, tam derleme adının kısa bir biçimi olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-152">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="8ca1a-153">Derlemenin yapısını ve amacını özetleyen kısa bir açıklama belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-153">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="8ca1a-154">Derleme için kolay bir ad belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-154">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="8ca1a-155">Örneğin, *Comdlg* adlı bir derlemede Microsoft ortak Iletişim kutusu denetimi başlığı bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-155">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="8ca1a-156">Tanımlayıcı ad öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="8ca1a-156">Strong name attributes</span></span>

<span data-ttu-id="8ca1a-157">Bir derleme için tanımlayıcı ad ayarlamak üzere tanımlayıcı ad öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-157">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="8ca1a-158">Aşağıdaki tabloda tanımlayıcı ad öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-158">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="8ca1a-159">Tanımlayıcı ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ca1a-159">Strong name attribute</span></span>|<span data-ttu-id="8ca1a-160">Description</span><span class="sxs-lookup"><span data-stu-id="8ca1a-160">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="8ca1a-161">Gecikme imzasının kullanıldığını gösteren Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-161">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="8ca1a-162">Ortak anahtar (gecikme imzalamayı kullanıyorsanız) veya bu özniteliğin oluşturucusuna parametre olarak geçirilen ortak ve özel anahtarları içeren dosyanın adını gösteren dize değeri.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-162">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="8ca1a-163">Dosya adının, kaynak dosya yolu değil çıkış dosyası yoluna ( *. exe* veya *. dll*) göreli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-163">Note that the file name is relative to the output file path (the *.exe* or *.dll*), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="8ca1a-164">Bu özniteliğin oluşturucusuna parametre olarak geçirilen anahtar çiftini içeren anahtar kapsayıcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-164">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="8ca1a-165">Aşağıdaki kod örneğinde, *MyKey. snk*adlı ortak anahtar dosyası ile tanımlayıcı adlı bir derleme oluşturmak için Gecikmeli imzalama kullanılırken uygulanacak Öznitelikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-165">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk*.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8ca1a-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ca1a-166">See also</span></span>

- [<span data-ttu-id="8ca1a-167">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ca1a-167">Create assemblies</span></span>](create.md)
