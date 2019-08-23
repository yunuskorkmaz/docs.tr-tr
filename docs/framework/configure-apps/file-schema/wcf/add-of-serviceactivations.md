---
title: <add> / <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920023"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="df4a6-102">\<\<serviceetkinleştirmeleri > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="df4a6-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="df4a6-103">Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlamanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="df4a6-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="df4a6-104">Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="df4a6-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="df4a6-105">\<sistemin. ServiceModel > </span><span class="sxs-lookup"><span data-stu-id="df4a6-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="df4a6-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="df4a6-106">\<serviceHostingEnvironment></span></span>

## <a name="syntax"></a><span data-ttu-id="df4a6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df4a6-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df4a6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="df4a6-108">Attributes and Elements</span></span>

<span data-ttu-id="df4a6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df4a6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="df4a6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="df4a6-110">Attributes</span></span>

|<span data-ttu-id="df4a6-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="df4a6-111">Attribute</span></span>|<span data-ttu-id="df4a6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df4a6-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="df4a6-113">Çar</span><span class="sxs-lookup"><span data-stu-id="df4a6-113">factory</span></span>|<span data-ttu-id="df4a6-114">Bir hizmet etkinleştirme öğesi üreten fabrika 'nin CLR türü adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="df4a6-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="df4a6-115">hizmet</span><span class="sxs-lookup"><span data-stu-id="df4a6-115">service</span></span>|<span data-ttu-id="df4a6-116">Hizmeti uygulayan ServiceType (tam nitelenmiş TypeName veya Short TypeName (App_Code klasörüne yerleştirildiğinde).</span><span class="sxs-lookup"><span data-stu-id="df4a6-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="df4a6-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="df4a6-117">relativeAddress</span></span>|<span data-ttu-id="df4a6-118">Geçerli IIS uygulamasındaki göreli adres (örneğin, "Service. svc").</span><span class="sxs-lookup"><span data-stu-id="df4a6-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="df4a6-119">WCF 4,0 ' de, bu göreli adresin bilinen dosya uzantılarından birini (. svc,. xamlx,...) içermesi gerekir. RelativeUrl 'Si için fiziksel dosya yok</span><span class="sxs-lookup"><span data-stu-id="df4a6-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="df4a6-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="df4a6-120">Child Elements</span></span>

<span data-ttu-id="df4a6-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="df4a6-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="df4a6-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="df4a6-122">Parent Elements</span></span>

|<span data-ttu-id="df4a6-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="df4a6-123">Element</span></span>|<span data-ttu-id="df4a6-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df4a6-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df4a6-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="df4a6-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="df4a6-126">Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="df4a6-126">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="df4a6-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df4a6-127">Remarks</span></span>

<span data-ttu-id="df4a6-128">Aşağıdaki örnek, Web. config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="df4a6-128">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="df4a6-129">Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df4a6-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="df4a6-130">Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="df4a6-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="df4a6-131">Yapılandırma `web.config` içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="df4a6-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="df4a6-132">Ayrıca, `serviceHostingEnvironment` bir MachineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="df4a6-132">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="df4a6-133">Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="df4a6-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="df4a6-134">Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="df4a6-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="df4a6-135">RelativeAddress, yani. svc,. xoml veya. xamlx için Uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="df4a6-135">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="df4a6-136">Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="df4a6-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="df4a6-137">Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="df4a6-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="df4a6-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df4a6-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
