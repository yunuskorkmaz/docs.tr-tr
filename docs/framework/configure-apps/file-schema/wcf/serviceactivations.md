---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936442"
---
# <a name="serviceactivations"></a><span data-ttu-id="4e52e-101">\<Serviceetkinleştirmeleri ></span><span class="sxs-lookup"><span data-stu-id="4e52e-101">\<serviceActivations></span></span>

<span data-ttu-id="4e52e-102">Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlayan ayarları eklemenize olanak tanıyan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="4e52e-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="4e52e-103">Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="4e52e-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="4e52e-104">\<sistemin. ServiceModel > </span><span class="sxs-lookup"><span data-stu-id="4e52e-104">\<system.ServiceModel></span></span>\
<span data-ttu-id="4e52e-105">\<serviceHostingEnvironment > </span><span class="sxs-lookup"><span data-stu-id="4e52e-105">\<serviceHostingEnvironment></span></span>\
<span data-ttu-id="4e52e-106">\<Serviceetkinleştirmeleri ></span><span class="sxs-lookup"><span data-stu-id="4e52e-106">\<serviceActivations></span></span>

## <a name="syntax"></a><span data-ttu-id="4e52e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e52e-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e52e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e52e-108">Attributes and Elements</span></span>

<span data-ttu-id="4e52e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4e52e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e52e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4e52e-110">Attributes</span></span>

<span data-ttu-id="4e52e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e52e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e52e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e52e-112">Child Elements</span></span>

|<span data-ttu-id="4e52e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="4e52e-113">Element</span></span>|<span data-ttu-id="4e52e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e52e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e52e-115">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="4e52e-115">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="4e52e-116">Bir hizmet uygulamasının etkinleştirilmesini belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="4e52e-116">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e52e-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4e52e-117">Parent Elements</span></span>

|<span data-ttu-id="4e52e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="4e52e-118">Element</span></span>|<span data-ttu-id="4e52e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e52e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e52e-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="4e52e-120">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="4e52e-121">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4e52e-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e52e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e52e-122">Remarks</span></span>

<span data-ttu-id="4e52e-123">Aşağıdaki örnek, Web. config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e52e-123">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="4e52e-124">Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e52e-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="4e52e-125">Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4e52e-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="4e52e-126">Yapılandırma `web.config` içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e52e-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="4e52e-127">Ayrıca, `serviceHostingEnvironment` bir MachineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="4e52e-127">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="4e52e-128">Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="4e52e-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="4e52e-129">Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="4e52e-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="4e52e-130">RelativeAddress (. svc,. xoml veya. xamlx) için Uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4e52e-130">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="4e52e-131">Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e52e-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="4e52e-132">Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4e52e-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e52e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e52e-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
