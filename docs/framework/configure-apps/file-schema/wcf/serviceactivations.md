---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 82422716482eafe996534e3bf1a94b4c7a604a6d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145126"
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="3f924-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="3f924-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="3f924-103">Windows Communication Foundation (WCF) hizmet türlerinizi eşleştiren sanal hizmet aktivasyon ayarlarını tanımlayan ayarları eklemenizi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="3f924-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="3f924-104">Bu WAS içinde barındırılan hizmetleri etkinleştirmeniz mümkün kılar / IIS .svc dosyası olmadan.</span><span class="sxs-lookup"><span data-stu-id="3f924-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="3f924-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3f924-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3f924-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="3f924-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="3f924-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="3f924-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f924-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f924-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f924-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f924-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f924-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f924-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f924-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f924-111">Attributes</span></span>  
 <span data-ttu-id="3f924-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f924-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f924-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f924-113">Child Elements</span></span>  
  
|<span data-ttu-id="3f924-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f924-114">Element</span></span>|<span data-ttu-id="3f924-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f924-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f924-116">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="3f924-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="3f924-117">Bir hizmet uygulaması etkinleştirme belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="3f924-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f924-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f924-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3f924-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f924-119">Element</span></span>|<span data-ttu-id="3f924-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f924-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f924-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="3f924-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="3f924-122">Belirli bir hizmet barındırma ortamını gösteren türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f924-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f924-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f924-123">Remarks</span></span>  
 <span data-ttu-id="3f924-124">Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3f924-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="3f924-125">Bu yapılandırmayı kullanarak .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f924-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="3f924-126">Unutmayın `<serviceHostingEnvironment>` uygulama düzeyinde yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="3f924-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="3f924-127">Yerleştirmek sahip olduğunuz `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren.</span><span class="sxs-lookup"><span data-stu-id="3f924-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="3f924-128">Ayrıca, `serviceHostingEnvironment` machinetoApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="3f924-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="3f924-129">Tek bir hizmette makine kökündeki kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.</span><span class="sxs-lookup"><span data-stu-id="3f924-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="3f924-130">Yapılandırma temelli etkinleştirme, etkinleştirme hem http hem de olmayan http protokolü üzerinden destekler.</span><span class="sxs-lookup"><span data-stu-id="3f924-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="3f924-131">Yani .svc, .xoml veya .xamlx relatativeAddress uzantılarında gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="3f924-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="3f924-132">Sonra hizmeti uzantıyı etkinleştirmek üzere olanak sağlayacak bilinen buildProviders kendi uzantılarınızı eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f924-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="3f924-133">Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3f924-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f924-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f924-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
