---
title: <disableFusionUpdatesFromADManager> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: c3971379b358ae16fc463df2b8d6288cf8881391
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205041"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="07f75-102">\<disableFusionUpdatesFromADManager> Öğesi</span><span class="sxs-lookup"><span data-stu-id="07f75-102">\<disableFusionUpdatesFromADManager> Element</span></span>

<span data-ttu-id="07f75-103">Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="07f75-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="07f75-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="07f75-104">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07f75-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="07f75-105">Attributes and Elements</span></span>  

 <span data-ttu-id="07f75-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07f75-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07f75-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07f75-107">Attributes</span></span>  
  
|<span data-ttu-id="07f75-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07f75-108">Attribute</span></span>|<span data-ttu-id="07f75-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07f75-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="07f75-110">enabled</span><span class="sxs-lookup"><span data-stu-id="07f75-110">enabled</span></span>|<span data-ttu-id="07f75-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07f75-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="07f75-112">Fusion ayarlarını geçersiz kılabilme özelliğinin devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="07f75-112">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="07f75-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07f75-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="07f75-114">Değer</span><span class="sxs-lookup"><span data-stu-id="07f75-114">Value</span></span>|<span data-ttu-id="07f75-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07f75-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07f75-116">0</span><span class="sxs-lookup"><span data-stu-id="07f75-116">0</span></span>|<span data-ttu-id="07f75-117">Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="07f75-117">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="07f75-118">Bu, .NET Framework 4 ' ün başladığı varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="07f75-118">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="07f75-119">1</span><span class="sxs-lookup"><span data-stu-id="07f75-119">1</span></span>|<span data-ttu-id="07f75-120">Fusion ayarlarını geçersiz kılma özelliğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="07f75-120">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="07f75-121">Bu, .NET Framework önceki sürümlerinin davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="07f75-121">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07f75-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="07f75-122">Child Elements</span></span>  

 <span data-ttu-id="07f75-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="07f75-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07f75-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="07f75-124">Parent Elements</span></span>  
  
|<span data-ttu-id="07f75-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="07f75-125">Element</span></span>|<span data-ttu-id="07f75-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07f75-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="07f75-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="07f75-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="07f75-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="07f75-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07f75-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07f75-129">Remarks</span></span>  

 <span data-ttu-id="07f75-130">.NET Framework 4 ' te başlayarak, varsayılan davranış, <xref:System.AppDomainManager> nesnenin <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> alt sınıflarınızdaki yöntemi uygulamanıza geçirilen nesnenin özelliğini veya yöntemini kullanarak yapılandırma ayarlarını geçersiz kılmasına izin vermesidir <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="07f75-130">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="07f75-131">Varsayılan uygulama etki alanı için, değiştirdiğiniz ayarlar uygulama yapılandırma dosyası tarafından belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="07f75-131">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="07f75-132">Diğer uygulama etki alanları için veya yöntemine geçirilen yapılandırma ayarlarını geçersiz kılarlar <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="07f75-132">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="07f75-133">İletilen yapılandırma bilgilerini ortadan kaldırmak için yeni yapılandırma bilgilerini geçirebilir ya da null ( `Nothing` Visual Basic) geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07f75-133">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="07f75-134">Yapılandırma bilgilerini hem özelliğine hem de yöntemine iletmeyin <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> .</span><span class="sxs-lookup"><span data-stu-id="07f75-134">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="07f75-135">Yapılandırma bilgilerini her ikisine de geçirirseniz, <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> yöntemi uygulama yapılandırma dosyasından yapılandırma bilgilerini geçersiz kıldığından, özelliğe geçirdiğiniz bilgiler göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="07f75-135">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="07f75-136"><xref:System.AppDomainSetup.ConfigurationFile%2A>Özelliğini kullanırsanız, `Nothing` <xref:System.AppDomainSetup.SetConfigurationBytes%2A> veya yöntemine yapılan çağrıda belirtilen yapılandırma baytlarını ortadan kaldırmak için yöntemine null (Visual Basic) geçirebilirsiniz <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="07f75-136">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="07f75-137">Yapılandırma bilgilerine ek olarak,,,,,,,,, <xref:System.AppDomainSetup> ,,,, ve, yöntemi uygulamanıza geçirilen nesne üzerinde aşağıdaki ayarları değiştirebilirsiniz <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> :,,,,, <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> , <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> , <xref:System.AppDomainSetup.DynamicBase%2A> , <xref:System.AppDomainSetup.LoaderOptimization%2A> ,,, <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> ve <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .</span><span class="sxs-lookup"><span data-stu-id="07f75-137">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="07f75-138">Öğesini kullanmaya alternatif olarak `<disableFusionUpdatesFromADManager>` , bir kayıt defteri ayarı oluşturarak veya bir ortam değişkenini ayarlayarak varsayılan davranışı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07f75-138">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="07f75-139">Kayıt defterinde, veya altında adlı bir DWORD değeri `COMPLUS_disableFusionUpdatesFromADManager` oluşturun `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework` ve değeri 1 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="07f75-139">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="07f75-140">Komut satırında, ortam değişkenini `COMPLUS_disableFusionUpdatesFromADManager` 1 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="07f75-140">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07f75-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="07f75-141">Example</span></span>  

 <span data-ttu-id="07f75-142">Aşağıdaki örnek, öğesini kullanarak Fusion ayarlarını geçersiz kılma yeteneğinin nasıl devre dışı bırakılacağını gösterir `<disableFusionUpdatesFromADManager>` .</span><span class="sxs-lookup"><span data-stu-id="07f75-142">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07f75-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07f75-143">See also</span></span>

- [<span data-ttu-id="07f75-144">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="07f75-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="07f75-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="07f75-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="07f75-146">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="07f75-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
