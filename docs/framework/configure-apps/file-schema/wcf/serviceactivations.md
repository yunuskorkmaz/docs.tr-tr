---
title: '&lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47a7d0984a5fafa7f03a589570e2a1aa2546dd8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="e5bdb-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="e5bdb-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="e5bdb-103">Eşlenen sanal hizmeti etkinleştirme ayarlarını tanımla ayarları eklemenizi sağlayan bir yapılandırma öğesi, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet türleri.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="e5bdb-104">Bu WAS içinde barındırılan hizmetlere etkinleştirmek mümkün kılar / IIS .svc dosyası olmadan.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="e5bdb-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e5bdb-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5bdb-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="e5bdb-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="e5bdb-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="e5bdb-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5bdb-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5bdb-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5bdb-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5bdb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e5bdb-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5bdb-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5bdb-111">Attributes</span></span>  
 <span data-ttu-id="e5bdb-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5bdb-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5bdb-113">Child Elements</span></span>  
  
|<span data-ttu-id="e5bdb-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5bdb-114">Element</span></span>|<span data-ttu-id="e5bdb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5bdb-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5bdb-116">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="e5bdb-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="e5bdb-117">Bir hizmet uygulaması etkinleştirme belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5bdb-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5bdb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e5bdb-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5bdb-119">Element</span></span>|<span data-ttu-id="e5bdb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5bdb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5bdb-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="e5bdb-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="e5bdb-122">Belirli bir barındırma ortamı hizmeti başlatır türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5bdb-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5bdb-123">Remarks</span></span>  
 <span data-ttu-id="e5bdb-124">Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="e5bdb-125">Bu yapılandırmayı kullanarak, bir .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="e5bdb-126">Unutmayın `<serviceHostingEnvironment>` uygulama düzeyi yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="e5bdb-127">Yerleştirmek zorunda `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="e5bdb-128">Ayrıca, `serviceHostingEnvironment` machinetoApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="e5bdb-129">Tek bir hizmeti makinenin kök dizininde kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="e5bdb-130">Yapılandırma temelli etkinleştirme hem http hem de http olmayan protokolü üzerinden etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="e5bdb-131">Yani .svc, .xoml veya .xamlx relatativeAddress uzantılarında gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="e5bdb-132">Ardından, uzantıyı hizmeti etkinleştirmek üzere olanak tanır bilinen buildProviders kendi uzantıları eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="e5bdb-133">Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtlar geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5bdb-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5bdb-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
