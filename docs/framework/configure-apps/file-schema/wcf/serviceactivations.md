---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: c62f2bd1a34aca31ea9f9d5de17840f2967b269c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="713bc-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="713bc-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="713bc-103">Windows Communication Foundation (WCF) hizmetini türlerinizi eşlenen sanal hizmeti etkinleştirme ayarlarını tanımla ayarları eklemenize izin verir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="713bc-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="713bc-104">Bu WAS içinde barındırılan hizmetlere etkinleştirmek mümkün kılar / IIS .svc dosyası olmadan.</span><span class="sxs-lookup"><span data-stu-id="713bc-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="713bc-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="713bc-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="713bc-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="713bc-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="713bc-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="713bc-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713bc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="713bc-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="713bc-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="713bc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="713bc-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="713bc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="713bc-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="713bc-111">Attributes</span></span>  
 <span data-ttu-id="713bc-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="713bc-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="713bc-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="713bc-113">Child Elements</span></span>  
  
|<span data-ttu-id="713bc-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="713bc-114">Element</span></span>|<span data-ttu-id="713bc-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="713bc-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="713bc-116">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="713bc-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="713bc-117">Bir hizmet uygulaması etkinleştirme belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="713bc-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="713bc-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="713bc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="713bc-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="713bc-119">Element</span></span>|<span data-ttu-id="713bc-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="713bc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="713bc-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="713bc-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="713bc-122">Belirli bir barındırma ortamı hizmeti başlatır türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="713bc-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="713bc-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="713bc-123">Remarks</span></span>  
 <span data-ttu-id="713bc-124">Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="713bc-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="713bc-125">Bu yapılandırmayı kullanarak, bir .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="713bc-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="713bc-126">Unutmayın `<serviceHostingEnvironment>` uygulama düzeyi yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="713bc-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="713bc-127">Yerleştirmek zorunda `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren.</span><span class="sxs-lookup"><span data-stu-id="713bc-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="713bc-128">Ayrıca, `serviceHostingEnvironment` machinetoApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="713bc-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="713bc-129">Tek bir hizmeti makinenin kök dizininde kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.</span><span class="sxs-lookup"><span data-stu-id="713bc-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="713bc-130">Yapılandırma temelli etkinleştirme hem http hem de http olmayan protokolü üzerinden etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="713bc-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="713bc-131">Yani .svc, .xoml veya .xamlx relatativeAddress uzantılarında gerektirir.</span><span class="sxs-lookup"><span data-stu-id="713bc-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="713bc-132">Ardından, uzantıyı hizmeti etkinleştirmek üzere olanak tanır bilinen buildProviders kendi uzantıları eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="713bc-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="713bc-133">Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtlar geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="713bc-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713bc-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="713bc-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
