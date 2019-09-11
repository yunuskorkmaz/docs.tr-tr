---
title: <add> / <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850322"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="52ece-102">\<\<serviceetkinleştirmeleri > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="52ece-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="52ece-103">Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlamanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="52ece-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="52ece-104">Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="52ece-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="52ece-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="52ece-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="52ece-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="52ece-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="52ece-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="52ece-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="52ece-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Serviceetkinleştirmeleri >** ](serviceactivations.md)</span><span class="sxs-lookup"><span data-stu-id="52ece-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)</span></span>\
<span data-ttu-id="52ece-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="52ece-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="52ece-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52ece-110">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52ece-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="52ece-111">Attributes and Elements</span></span>

<span data-ttu-id="52ece-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52ece-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="52ece-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52ece-113">Attributes</span></span>

|<span data-ttu-id="52ece-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52ece-114">Attribute</span></span>|<span data-ttu-id="52ece-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52ece-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="52ece-116">Çar</span><span class="sxs-lookup"><span data-stu-id="52ece-116">factory</span></span>|<span data-ttu-id="52ece-117">Bir hizmet etkinleştirme öğesi üreten fabrika 'nin CLR türü adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="52ece-117">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="52ece-118">hizmet</span><span class="sxs-lookup"><span data-stu-id="52ece-118">service</span></span>|<span data-ttu-id="52ece-119">Hizmeti uygulayan ServiceType (tam nitelenmiş TypeName veya Short TypeName (App_Code klasörüne yerleştirildiğinde).</span><span class="sxs-lookup"><span data-stu-id="52ece-119">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="52ece-120">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="52ece-120">relativeAddress</span></span>|<span data-ttu-id="52ece-121">Geçerli IIS uygulamasındaki göreli adres (örneğin, "Service. svc").</span><span class="sxs-lookup"><span data-stu-id="52ece-121">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="52ece-122">WCF 4,0 ' de, bu göreli adresin bilinen dosya uzantılarından birini (. svc,. xamlx,...) içermesi gerekir. RelativeUrl 'Si için fiziksel dosya yok</span><span class="sxs-lookup"><span data-stu-id="52ece-122">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="52ece-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="52ece-123">Child Elements</span></span>

<span data-ttu-id="52ece-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="52ece-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="52ece-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="52ece-125">Parent Elements</span></span>

|<span data-ttu-id="52ece-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="52ece-126">Element</span></span>|<span data-ttu-id="52ece-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52ece-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52ece-128">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="52ece-128">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="52ece-129">Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="52ece-129">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52ece-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52ece-130">Remarks</span></span>

<span data-ttu-id="52ece-131">Aşağıdaki örnek, Web. config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="52ece-131">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="52ece-132">Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52ece-132">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="52ece-133">Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="52ece-133">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="52ece-134">Yapılandırma `web.config` içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="52ece-134">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="52ece-135">Ayrıca, `serviceHostingEnvironment` bir MachineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="52ece-135">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="52ece-136">Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="52ece-136">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="52ece-137">Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="52ece-137">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="52ece-138">RelativeAddress, yani. svc,. xoml veya. xamlx için Uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="52ece-138">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="52ece-139">Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="52ece-139">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="52ece-140">Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="52ece-140">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="52ece-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52ece-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
