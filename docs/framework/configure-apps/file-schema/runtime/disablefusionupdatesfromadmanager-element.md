---
title: <disableFusionUpdatesFromADManager> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b65711ad8c404d1c4f54a6197faf598e2215226f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252658"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="33723-102">\<disableFusionUpdatesFromADManager > öğesi</span><span class="sxs-lookup"><span data-stu-id="33723-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="33723-103">Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33723-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
<span data-ttu-id="33723-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="33723-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="33723-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="33723-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="33723-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableFusionUpdatesFromADManager >**</span><span class="sxs-lookup"><span data-stu-id="33723-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33723-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33723-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33723-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="33723-108">Attributes and Elements</span></span>  
 <span data-ttu-id="33723-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33723-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33723-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="33723-110">Attributes</span></span>  
  
|<span data-ttu-id="33723-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="33723-111">Attribute</span></span>|<span data-ttu-id="33723-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33723-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33723-113">enabled</span><span class="sxs-lookup"><span data-stu-id="33723-113">enabled</span></span>|<span data-ttu-id="33723-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="33723-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="33723-115">Fusion ayarlarını geçersiz kılabilme özelliğinin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33723-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="33723-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="33723-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="33723-117">Değer</span><span class="sxs-lookup"><span data-stu-id="33723-117">Value</span></span>|<span data-ttu-id="33723-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33723-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="33723-119">0</span><span class="sxs-lookup"><span data-stu-id="33723-119">0</span></span>|<span data-ttu-id="33723-120">Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="33723-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="33723-121">Bu, .NET Framework 4 ' ün başladığı varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="33723-121">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="33723-122">1\.</span><span class="sxs-lookup"><span data-stu-id="33723-122">1</span></span>|<span data-ttu-id="33723-123">Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="33723-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="33723-124">Bu, .NET Framework önceki sürümlerinin davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="33723-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33723-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="33723-125">Child Elements</span></span>  
 <span data-ttu-id="33723-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="33723-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33723-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="33723-127">Parent Elements</span></span>  
  
|<span data-ttu-id="33723-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="33723-128">Element</span></span>|<span data-ttu-id="33723-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33723-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="33723-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="33723-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="33723-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="33723-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33723-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33723-132">Remarks</span></span>  
 <span data-ttu-id="33723-133">.NET Framework 4 ' te başlayarak, varsayılan <xref:System.AppDomainManager> davranış, nesnenin, uygulamanıza geçirilen <xref:System.AppDomainSetup> nesnenin <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliğini veya <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemini kullanarak yapılandırma ayarlarını geçersiz kılmasına izin vermesidir , kendi<xref:System.AppDomainManager>alt sınıfdaki <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="33723-133">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="33723-134">Varsayılan uygulama etki alanı için, değiştirdiğiniz ayarlar uygulama yapılandırma dosyası tarafından belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="33723-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="33723-135">Diğer uygulama etki alanları için <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yöntemine geçirilen yapılandırma ayarlarını geçersiz kılarlar.</span><span class="sxs-lookup"><span data-stu-id="33723-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="33723-136">İletilen yapılandırma bilgilerini ortadan kaldırmak için yeni yapılandırma bilgilerini geçirebilir ya da`Nothing` null (Visual Basic) geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33723-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="33723-137">Yapılandırma bilgilerini hem <xref:System.AppDomainSetup.ConfigurationFile%2A> özelliğine <xref:System.AppDomainSetup.SetConfigurationBytes%2A> hem de yöntemine iletmeyin.</span><span class="sxs-lookup"><span data-stu-id="33723-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="33723-138">Yapılandırma bilgilerini her ikisine de geçirirseniz, <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi uygulama yapılandırma dosyasından yapılandırma bilgilerini geçersiz kıldığından, özelliğe geçirdiğiniz bilgiler göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="33723-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="33723-139"><xref:System.AppDomainSetup.ConfigurationFile%2A> Özelliğini kullanırsanız, <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> veya <xref:System.AppDomainSetup.SetConfigurationBytes%2A> `Nothing` yöntemine<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> yapılan çağrıda belirtilen yapılandırma baytlarını ortadan kaldırmak için yöntemine null (Visual Basic) geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33723-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="33723-140">Yapılandırma <xref:System.AppDomainSetup> bilgilerine ek olarak, <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.ApplicationBase%2A> yöntemiuygulamanızageçirilennesne<xref:System.AppDomainSetup.DisallowBindingRedirects%2A> üzerinde aşağıdaki ayarları değiştirebilirsiniz:,,,, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> ,,<xref:System.AppDomainSetup.LoaderOptimization%2A>, ,,<xref:System.AppDomainSetup.PrivateBinPath%2A>, ,<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, ve<xref:System.AppDomainSetup.ShadowCopyFiles%2A>. <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A></span><span class="sxs-lookup"><span data-stu-id="33723-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="33723-141">`<disableFusionUpdatesFromADManager>` Öğesini kullanmaya alternatif olarak, bir kayıt defteri ayarı oluşturarak veya bir ortam değişkenini ayarlayarak varsayılan davranışı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33723-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="33723-142">Kayıt defterinde, veya `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework`altında adlı bir DWORD değeri oluşturun ve değeri 1 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="33723-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="33723-143">Komut satırında, ortam değişkenini `COMPLUS_disableFusionUpdatesFromADManager` 1 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="33723-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33723-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="33723-144">Example</span></span>  
 <span data-ttu-id="33723-145">Aşağıdaki örnek, `<disableFusionUpdatesFromADManager>` öğesini kullanarak Fusion ayarlarını geçersiz kılma yeteneğinin nasıl devre dışı bırakılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="33723-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33723-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33723-146">See also</span></span>

- [<span data-ttu-id="33723-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="33723-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="33723-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="33723-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="33723-149">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="33723-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
