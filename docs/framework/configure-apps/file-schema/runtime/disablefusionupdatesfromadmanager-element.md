---
description: 'Daha fazla bilgi edinin: <disableFusionUpdatesFromADManager> öğesi'
title: <disableFusionUpdatesFromADManager> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: c3b5758a12fc78c67ec0a4a9631361808724e72a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787090"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="3c44a-103">\<disableFusionUpdatesFromADManager> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3c44a-103">\<disableFusionUpdatesFromADManager> Element</span></span>

<span data-ttu-id="3c44a-104">Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c44a-104">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="3c44a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c44a-105">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c44a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c44a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3c44a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c44a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c44a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c44a-108">Attributes</span></span>  
  
|<span data-ttu-id="3c44a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3c44a-109">Attribute</span></span>|<span data-ttu-id="3c44a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c44a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c44a-111">enabled</span><span class="sxs-lookup"><span data-stu-id="3c44a-111">enabled</span></span>|<span data-ttu-id="3c44a-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3c44a-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="3c44a-113">Fusion ayarlarını geçersiz kılabilme özelliğinin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c44a-113">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3c44a-114">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3c44a-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="3c44a-115">Değer</span><span class="sxs-lookup"><span data-stu-id="3c44a-115">Value</span></span>|<span data-ttu-id="3c44a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c44a-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3c44a-117">0</span><span class="sxs-lookup"><span data-stu-id="3c44a-117">0</span></span>|<span data-ttu-id="3c44a-118">Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="3c44a-118">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="3c44a-119">Bu, .NET Framework 4 ' ün başladığı varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="3c44a-119">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="3c44a-120">1</span><span class="sxs-lookup"><span data-stu-id="3c44a-120">1</span></span>|<span data-ttu-id="3c44a-121">Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="3c44a-121">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="3c44a-122">Bu, .NET Framework önceki sürümlerinin davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="3c44a-122">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c44a-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c44a-123">Child Elements</span></span>  

 <span data-ttu-id="3c44a-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c44a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c44a-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c44a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3c44a-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c44a-126">Element</span></span>|<span data-ttu-id="3c44a-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c44a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3c44a-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3c44a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3c44a-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3c44a-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c44a-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c44a-130">Remarks</span></span>  

 <span data-ttu-id="3c44a-131">.NET Framework 4 ' te başlayarak, varsayılan davranış, <xref:System.AppDomainManager> nesnenin <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> alt sınıflarınızdaki yöntemi uygulamanıza geçirilen nesnenin özelliğini veya yöntemini kullanarak yapılandırma ayarlarını geçersiz kılmasına izin vermesidir <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="3c44a-131">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="3c44a-132">Varsayılan uygulama etki alanı için, değiştirdiğiniz ayarlar uygulama yapılandırma dosyası tarafından belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3c44a-132">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="3c44a-133">Diğer uygulama etki alanları için veya yöntemine geçirilen yapılandırma ayarlarını geçersiz kılarlar <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3c44a-133">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3c44a-134">İletilen yapılandırma bilgilerini ortadan kaldırmak için yeni yapılandırma bilgilerini geçirebilir ya da null ( `Nothing` Visual Basic) geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c44a-134">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="3c44a-135">Yapılandırma bilgilerini hem özelliğine hem de yöntemine iletmeyin <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> .</span><span class="sxs-lookup"><span data-stu-id="3c44a-135">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="3c44a-136">Yapılandırma bilgilerini her ikisine de geçirirseniz, <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi uygulama yapılandırma dosyasından yapılandırma bilgilerini geçersiz kıldığından, özelliğe geçirdiğiniz bilgiler göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="3c44a-136">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="3c44a-137"><xref:System.AppDomainSetup.ConfigurationFile%2A>Özelliğini kullanırsanız, `Nothing` <xref:System.AppDomainSetup.SetConfigurationBytes%2A> veya yöntemine yapılan çağrıda belirtilen yapılandırma baytlarını ortadan kaldırmak için yöntemine null (Visual Basic) geçirebilirsiniz <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3c44a-137">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3c44a-138">Yapılandırma bilgilerine ek olarak,,,,,,,,, <xref:System.AppDomainSetup> ,,,, ve, yöntemi uygulamanıza geçirilen nesne üzerinde aşağıdaki ayarları değiştirebilirsiniz <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> :,,,,, <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> , <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> , <xref:System.AppDomainSetup.DynamicBase%2A> , <xref:System.AppDomainSetup.LoaderOptimization%2A> ,,, <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> ve <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .</span><span class="sxs-lookup"><span data-stu-id="3c44a-138">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="3c44a-139">Öğesini kullanmaya alternatif olarak `<disableFusionUpdatesFromADManager>` , bir kayıt defteri ayarı oluşturarak veya bir ortam değişkenini ayarlayarak varsayılan davranışı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c44a-139">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="3c44a-140">Kayıt defterinde, veya altında adlı bir DWORD değeri `COMPLUS_disableFusionUpdatesFromADManager` oluşturun `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework` ve değeri 1 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3c44a-140">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="3c44a-141">Komut satırında, ortam değişkenini `COMPLUS_disableFusionUpdatesFromADManager` 1 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3c44a-141">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c44a-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c44a-142">Example</span></span>  

 <span data-ttu-id="3c44a-143">Aşağıdaki örnek, öğesini kullanarak Fusion ayarlarını geçersiz kılma yeteneğinin nasıl devre dışı bırakılacağını gösterir `<disableFusionUpdatesFromADManager>` .</span><span class="sxs-lookup"><span data-stu-id="3c44a-143">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c44a-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c44a-144">See also</span></span>

- [<span data-ttu-id="3c44a-145">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="3c44a-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3c44a-146">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="3c44a-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3c44a-147">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="3c44a-147">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
