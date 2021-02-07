---
description: 'Hakkında daha fazla bilgi <add> edinin: <serviceActivations>'
title: <add> / <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 53c89321c8cde1966a04870c62fa0777610ff547
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750149"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="6a987-103">\<add> / \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="6a987-103">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="6a987-104">Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlamanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a987-104">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="6a987-105">Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="6a987-105">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="6a987-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a987-106">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a987-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a987-107">Attributes and Elements</span></span>

<span data-ttu-id="6a987-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a987-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a987-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a987-109">Attributes</span></span>

|<span data-ttu-id="6a987-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6a987-110">Attribute</span></span>|<span data-ttu-id="6a987-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a987-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6a987-112">Çar</span><span class="sxs-lookup"><span data-stu-id="6a987-112">factory</span></span>|<span data-ttu-id="6a987-113">Bir hizmet etkinleştirme öğesi üreten fabrika 'nin CLR türü adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6a987-113">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="6a987-114">hizmet</span><span class="sxs-lookup"><span data-stu-id="6a987-114">service</span></span>|<span data-ttu-id="6a987-115">Hizmeti uygulayan ServiceType (tam nitelenmiş TypeName veya Short TypeName (App_Code klasörüne yerleştirildiğinde).</span><span class="sxs-lookup"><span data-stu-id="6a987-115">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="6a987-116">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="6a987-116">relativeAddress</span></span>|<span data-ttu-id="6a987-117">Geçerli IIS uygulamasındaki göreli adres (örneğin, "Service. svc").</span><span class="sxs-lookup"><span data-stu-id="6a987-117">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="6a987-118">WCF 4,0 ' de, bu göreli adresin bilinen dosya uzantılarından birini (. svc,. xamlx,...) içermesi gerekir. RelativeUrl 'Si için fiziksel dosya yok</span><span class="sxs-lookup"><span data-stu-id="6a987-118">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6a987-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a987-119">Child Elements</span></span>

<span data-ttu-id="6a987-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a987-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a987-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a987-121">Parent Elements</span></span>

|<span data-ttu-id="6a987-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a987-122">Element</span></span>|<span data-ttu-id="6a987-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a987-123">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="6a987-124">Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="6a987-124">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a987-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a987-125">Remarks</span></span>

<span data-ttu-id="6a987-126">Aşağıdaki örnek, web.config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a987-126">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="6a987-127">Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a987-127">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="6a987-128">Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6a987-128">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="6a987-129">`web.config`Yapılandırma içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a987-129">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="6a987-130">Ayrıca, `serviceHostingEnvironment` bir machineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="6a987-130">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="6a987-131">Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="6a987-131">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="6a987-132">Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="6a987-132">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="6a987-133">RelativeAddress, yani. svc,. xoml veya. xamlx için Uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6a987-133">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="6a987-134">Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a987-134">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="6a987-135">Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6a987-135">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a987-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a987-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
