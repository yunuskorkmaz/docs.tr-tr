---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 7506cce61966a4a4650ff591cd6106dfd4a33b67
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680418"
---
# <a name="serviceactivations"></a><span data-ttu-id="82637-101">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="82637-101">\<serviceActivations></span></span>

<span data-ttu-id="82637-102">Windows Communication Foundation (WCF) hizmet türlerinizi eşleştiren sanal hizmet aktivasyon ayarlarını tanımlayan ayarları eklemenizi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="82637-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="82637-103">Bu WAS içinde barındırılan hizmetleri etkinleştirmeniz mümkün kılar / IIS .svc dosyası olmadan.</span><span class="sxs-lookup"><span data-stu-id="82637-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="82637-104">\<sistemi. ServiceModel > \\</span><span class="sxs-lookup"><span data-stu-id="82637-104">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="82637-105">\<serviceHostingEnvironment > \\</span><span class="sxs-lookup"><span data-stu-id="82637-105">\<serviceHostingEnvironment>\\</span></span>
<span data-ttu-id="82637-106">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="82637-106">\<serviceActivations></span></span>

## <a name="syntax"></a><span data-ttu-id="82637-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82637-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82637-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="82637-108">Attributes and Elements</span></span>

<span data-ttu-id="82637-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82637-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="82637-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82637-110">Attributes</span></span>

<span data-ttu-id="82637-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="82637-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="82637-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="82637-112">Child Elements</span></span>

|<span data-ttu-id="82637-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="82637-113">Element</span></span>|<span data-ttu-id="82637-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82637-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82637-115">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="82637-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="82637-116">Bir hizmet uygulaması etkinleştirme belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="82637-116">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="82637-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="82637-117">Parent Elements</span></span>

|<span data-ttu-id="82637-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="82637-118">Element</span></span>|<span data-ttu-id="82637-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82637-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82637-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="82637-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="82637-121">Belirli bir hizmet barındırma ortamını gösteren türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82637-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82637-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82637-122">Remarks</span></span>

<span data-ttu-id="82637-123">Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82637-123">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="82637-124">Bu yapılandırmayı kullanarak .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82637-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="82637-125">Unutmayın `<serviceHostingEnvironment>` uygulama düzeyinde yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="82637-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="82637-126">Yerleştirmek sahip olduğunuz `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren.</span><span class="sxs-lookup"><span data-stu-id="82637-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="82637-127">Ayrıca, `serviceHostingEnvironment` machineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="82637-127">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="82637-128">Tek bir hizmette makine kökündeki kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.</span><span class="sxs-lookup"><span data-stu-id="82637-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="82637-129">Yapılandırma temelli etkinleştirme, etkinleştirme hem http hem de olmayan http protokolü üzerinden destekler.</span><span class="sxs-lookup"><span data-stu-id="82637-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="82637-130">Yani .svc, .xoml veya .xamlx relativeAddress uzantılarında gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="82637-130">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="82637-131">Sonra hizmeti uzantıyı etkinleştirmek üzere olanak sağlayacak bilinen buildProviders kendi uzantılarınızı eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82637-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="82637-132">Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="82637-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="82637-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82637-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
