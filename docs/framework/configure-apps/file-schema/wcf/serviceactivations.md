---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855139"
---
# <a name="serviceactivations"></a><span data-ttu-id="e1d15-101">\<Serviceetkinleştirmeleri ></span><span class="sxs-lookup"><span data-stu-id="e1d15-101">\<serviceActivations></span></span>

<span data-ttu-id="e1d15-102">Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlayan ayarları eklemenize olanak tanıyan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e1d15-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="e1d15-103">Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="e1d15-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="e1d15-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e1d15-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e1d15-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e1d15-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e1d15-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="e1d15-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="e1d15-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Serviceetkinleştirmeleri >**</span><span class="sxs-lookup"><span data-stu-id="e1d15-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="e1d15-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1d15-108">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1d15-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1d15-109">Attributes and Elements</span></span>

<span data-ttu-id="e1d15-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1d15-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1d15-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e1d15-111">Attributes</span></span>

<span data-ttu-id="e1d15-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e1d15-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1d15-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1d15-113">Child Elements</span></span>

|<span data-ttu-id="e1d15-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1d15-114">Element</span></span>|<span data-ttu-id="e1d15-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1d15-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1d15-116">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="e1d15-116">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="e1d15-117">Bir hizmet uygulamasının etkinleştirilmesini belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="e1d15-117">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e1d15-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1d15-118">Parent Elements</span></span>

|<span data-ttu-id="e1d15-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1d15-119">Element</span></span>|<span data-ttu-id="e1d15-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1d15-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1d15-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="e1d15-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="e1d15-122">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e1d15-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1d15-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1d15-123">Remarks</span></span>

<span data-ttu-id="e1d15-124">Aşağıdaki örnek, Web. config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1d15-124">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="e1d15-125">Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1d15-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="e1d15-126">Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1d15-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="e1d15-127">Yapılandırma `web.config` içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1d15-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="e1d15-128">Ayrıca, `serviceHostingEnvironment` bir MachineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="e1d15-128">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="e1d15-129">Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1d15-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="e1d15-130">Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="e1d15-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="e1d15-131">RelativeAddress (. svc,. xoml veya. xamlx) için Uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1d15-131">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="e1d15-132">Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1d15-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="e1d15-133">Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e1d15-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1d15-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1d15-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
