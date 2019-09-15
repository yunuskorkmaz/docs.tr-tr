---
title: Derleme özniteliklerini ayarla
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d0809ec3da5a12abe950e63f9665037323a0ab39
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991675"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="12900-102">Derleme özniteliklerini ayarla</span><span class="sxs-lookup"><span data-stu-id="12900-102">Set assembly attributes</span></span>

<span data-ttu-id="12900-103">Derleme öznitelikleri, bir derleme hakkında bilgi sağlayan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="12900-103">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="12900-104">Öznitelikler aşağıdaki bilgi kümelerine ayrılır:</span><span class="sxs-lookup"><span data-stu-id="12900-104">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="12900-105">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="12900-105">Assembly identity attributes</span></span>

- <span data-ttu-id="12900-106">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12900-106">Informational attributes</span></span>

- <span data-ttu-id="12900-107">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="12900-107">Assembly manifest attributes</span></span>

- <span data-ttu-id="12900-108">Tanımlayıcı ad öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="12900-108">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="12900-109">Bütünleştirilmiş kod kimliği öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="12900-109">Assembly identity attributes</span></span>

<span data-ttu-id="12900-110">Bir tanımlayıcı ad (varsa) ile birlikte üç öznitelik, bir derlemenin kimliğini belirleme: ad, sürüm ve kültür.</span><span class="sxs-lookup"><span data-stu-id="12900-110">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="12900-111">Bu öznitelikler, derlemenin tam adını oluşturur ve koddaki derlemeye başvurulduğunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="12900-111">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="12900-112">Öznitelikleri, bir derlemenin sürümünü ve kültürünü ayarlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12900-112">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="12900-113">Derleyici veya [derleme Bağlayıcısı (al. exe)](../../framework/tools/al-exe-assembly-linker.md) , derleme bildirimini içeren dosyaya bağlı olarak, derleme oluşturulduğunda ad değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12900-113">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="12900-114">Aşağıdaki tabloda sürüm ve kültür öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12900-114">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="12900-115">Bütünleştirilmiş kod kimliği özniteliği</span><span class="sxs-lookup"><span data-stu-id="12900-115">Assembly identity attribute</span></span>|<span data-ttu-id="12900-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12900-116">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="12900-117">Derlemenin desteklediği kültürü gösteren numaralandırılmış alan.</span><span class="sxs-lookup"><span data-stu-id="12900-117">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="12900-118">Bir bütünleştirilmiş kod ayrıca kültür bağımsızlığını belirtebilir ve bu, varsayılan kültürün kaynaklarını içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="12900-118">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="12900-119">**Not:**  Çalışma zamanı, kültür özniteliği olmayan herhangi bir derlemeyi uydu derlemesi olarak null olarak ayarlanmış şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="12900-119">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="12900-120">Bu tür derlemeler uydu derleme bağlama kurallarına tabidir.</span><span class="sxs-lookup"><span data-stu-id="12900-120">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="12900-121">Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="12900-121">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="12900-122">Derlemenin yan yana çalıştırılıp çalıştırılmayacağı gibi, derleme özniteliklerini ayarlayan değer.</span><span class="sxs-lookup"><span data-stu-id="12900-122">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="12900-123">*Birincil*biçimdeki sayısal değer. *küçük*. *oluşturun*. *Düzeltme* (örneğin, 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="12900-123">Numeric value in the format *major*.*minor*.*build*.*revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="12900-124">Ortak dil çalışma zamanı, tanımlayıcı adlı derlemelerde bağlama işlemleri gerçekleştirmek için bu değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="12900-124">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="12900-125">**Not:**  <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> Özniteliği bir derlemeye uygulanmadığından, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği tarafından belirtilen sürüm numarası,, ve özellikleri tarafından kullanılır. <xref:System.Reflection.AssemblyInformationalVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="12900-125">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="12900-126">Aşağıdaki kod örneği, bir derlemeye sürüm ve kültür özniteliklerinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="12900-126">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

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

## <a name="informational-attributes"></a><span data-ttu-id="12900-127">Bilgilendirici öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12900-127">Informational attributes</span></span>

<span data-ttu-id="12900-128">Bir derlemeye ek şirket veya ürün bilgileri sağlamak için bilgilendirici öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12900-128">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="12900-129">Aşağıdaki tabloda, bir derlemeye uygulayabileceğiniz bilgilendirici öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12900-129">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="12900-130">Bilgilendirici özniteliği</span><span class="sxs-lookup"><span data-stu-id="12900-130">Informational attribute</span></span>|<span data-ttu-id="12900-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12900-131">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="12900-132">Şirket adını belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-132">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="12900-133">Telif hakkı bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-133">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="12900-134">Win32 dosya sürümü numarasını belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-134">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="12900-135">Bu, normalde derleme sürümünü varsayılan olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="12900-135">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="12900-136">Tam ürün sürümü numarası gibi ortak dil çalışma zamanı tarafından kullanılmayan sürüm bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-136">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="12900-137">**Not:**  Bu öznitelik bir derlemeye uygulanırsa, belirttiği dize <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> özelliği kullanılarak çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="12900-137">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="12900-138">Dize, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> özellikleri tarafından sunulan yol ve kayıt defteri anahtarında de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12900-138">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="12900-139">Ürün bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-139">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="12900-140">Ticari marka bilgilerini belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-140">String value specifying trademark information.</span></span>|

<span data-ttu-id="12900-141">Bu öznitelikler, derlemenin Windows özellikleri sayfasında görünebilir veya kendi Win32 kaynak dosyanızı belirtmek için **/win32res** derleyici seçeneği kullanılarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="12900-141">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="12900-142">Bütünleştirilmiş kod bildirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="12900-142">Assembly manifest attributes</span></span>

<span data-ttu-id="12900-143">Derleme bildiriminde başlık, açıklama, varsayılan diğer ad ve yapılandırma dahil olmak üzere bilgi sağlamak için bütünleştirilmiş kod bildirim özniteliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12900-143">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="12900-144">Aşağıdaki tabloda, derleme bildirim öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12900-144">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="12900-145">Bütünleştirilmiş kod bildirim özniteliği</span><span class="sxs-lookup"><span data-stu-id="12900-145">Assembly manifest attribute</span></span>|<span data-ttu-id="12900-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12900-146">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="12900-147">Derlemenin, perakende veya hata ayıklama gibi yapılandırmasını gösteren dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-147">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="12900-148">Çalışma zamanı bu değeri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="12900-148">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="12900-149">Başvurulan derlemelere göre kullanılacak varsayılan bir diğer ad belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-149">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="12900-150">Bu değer, derlemenin kendisinin adı kolay değil (bir GUID değeri gibi) kolay bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="12900-150">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="12900-151">Bu değer, tam derleme adının kısa bir biçimi olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12900-151">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="12900-152">Derlemenin yapısını ve amacını özetleyen kısa bir açıklama belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-152">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="12900-153">Derleme için kolay bir ad belirten dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-153">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="12900-154">Örneğin, *Comdlg* adlı bir derlemede Microsoft ortak Iletişim kutusu denetimi başlığı bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="12900-154">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="12900-155">Tanımlayıcı ad öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="12900-155">Strong name attributes</span></span>

<span data-ttu-id="12900-156">Bir derleme için tanımlayıcı ad ayarlamak üzere tanımlayıcı ad öznitelikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12900-156">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="12900-157">Aşağıdaki tabloda tanımlayıcı ad öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12900-157">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="12900-158">Tanımlayıcı ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="12900-158">Strong name attribute</span></span>|<span data-ttu-id="12900-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12900-159">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="12900-160">Gecikme imzasının kullanıldığını gösteren Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-160">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="12900-161">Ortak anahtar (gecikme imzalamayı kullanıyorsanız) veya bu özniteliğin oluşturucusuna parametre olarak geçirilen ortak ve özel anahtarları içeren dosyanın adını gösteren dize değeri.</span><span class="sxs-lookup"><span data-stu-id="12900-161">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="12900-162">Dosya adının, kaynak dosya yolu değil çıkış dosyası yoluna ( *. exe* veya *. dll*) göreli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="12900-162">Note that the file name is relative to the output file path (the *.exe* or *.dll*), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="12900-163">Bu özniteliğin oluşturucusuna parametre olarak geçirilen anahtar çiftini içeren anahtar kapsayıcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="12900-163">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="12900-164">Aşağıdaki kod örneğinde, *MyKey. snk*adlı ortak anahtar dosyası ile tanımlayıcı adlı bir derleme oluşturmak için Gecikmeli imzalama kullanılırken uygulanacak Öznitelikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="12900-164">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk*.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="12900-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12900-165">See also</span></span>

- [<span data-ttu-id="12900-166">Derlemeler oluştur</span><span class="sxs-lookup"><span data-stu-id="12900-166">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="12900-167">Bütünleştirilmiş kod içeren program</span><span class="sxs-lookup"><span data-stu-id="12900-167">Program with assemblies</span></span>](program.md)
