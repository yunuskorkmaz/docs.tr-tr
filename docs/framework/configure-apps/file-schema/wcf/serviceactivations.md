---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855139"
---
# \<serviceActivations>

<span data-ttu-id="0b5cc-101">Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlayan ayarları eklemenize olanak tanıyan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-101">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="0b5cc-102">Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-102">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="0b5cc-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b5cc-103">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b5cc-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5cc-104">Attributes and Elements</span></span>

<span data-ttu-id="0b5cc-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b5cc-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b5cc-106">Attributes</span></span>

<span data-ttu-id="0b5cc-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-107">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b5cc-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5cc-108">Child Elements</span></span>

|<span data-ttu-id="0b5cc-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b5cc-109">Element</span></span>|<span data-ttu-id="0b5cc-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b5cc-110">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="0b5cc-111">Bir hizmet uygulamasının etkinleştirilmesini belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-111">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0b5cc-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5cc-112">Parent Elements</span></span>

|<span data-ttu-id="0b5cc-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b5cc-113">Element</span></span>|<span data-ttu-id="0b5cc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b5cc-114">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="0b5cc-115">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b5cc-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b5cc-116">Remarks</span></span>

<span data-ttu-id="0b5cc-117">Aşağıdaki örnek, Web. config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-117">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="0b5cc-118">Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-118">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="0b5cc-119">Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-119">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="0b5cc-120">`web.config`Yapılandırma içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-120">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="0b5cc-121">Ayrıca, `serviceHostingEnvironment` bir machineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-121">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="0b5cc-122">Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-122">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="0b5cc-123">Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-123">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="0b5cc-124">RelativeAddress (. svc,. xoml veya. xamlx) için Uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-124">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="0b5cc-125">Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-125">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="0b5cc-126">Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-126">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b5cc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
