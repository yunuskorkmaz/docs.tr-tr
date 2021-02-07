---
description: 'Hakkında daha fazla bilgi edinin: <serviceActivations>'
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 726514af4e42cc387daf61b688d528f690ec8ee8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683027"
---
# \<serviceActivations>

<span data-ttu-id="eec02-102">Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlayan ayarları eklemenize olanak tanıyan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="eec02-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="eec02-103">Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="eec02-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="eec02-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="eec02-104">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eec02-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eec02-105">Attributes and Elements</span></span>

<span data-ttu-id="eec02-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eec02-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="eec02-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eec02-107">Attributes</span></span>

<span data-ttu-id="eec02-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="eec02-108">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eec02-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eec02-109">Child Elements</span></span>

|<span data-ttu-id="eec02-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="eec02-110">Element</span></span>|<span data-ttu-id="eec02-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eec02-111">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="eec02-112">Bir hizmet uygulamasının etkinleştirilmesini belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="eec02-112">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eec02-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eec02-113">Parent Elements</span></span>

|<span data-ttu-id="eec02-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="eec02-114">Element</span></span>|<span data-ttu-id="eec02-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eec02-115">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="eec02-116">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eec02-116">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eec02-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eec02-117">Remarks</span></span>

<span data-ttu-id="eec02-118">Aşağıdaki örnek, web.config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eec02-118">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="eec02-119">Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eec02-119">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="eec02-120">Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eec02-120">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="eec02-121">`web.config`Yapılandırma içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eec02-121">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="eec02-122">Ayrıca, `serviceHostingEnvironment` bir machineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="eec02-122">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="eec02-123">Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="eec02-123">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="eec02-124">Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="eec02-124">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="eec02-125">RelativeAddress (. svc,. xoml veya. xamlx) için Uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="eec02-125">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="eec02-126">Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="eec02-126">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="eec02-127">Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="eec02-127">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="eec02-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eec02-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
