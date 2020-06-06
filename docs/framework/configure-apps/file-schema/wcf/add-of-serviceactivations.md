---
title: <add> / <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850322"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="ebd73-102">\<add> / \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="ebd73-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="ebd73-103">Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlamanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ebd73-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="ebd73-104">Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="ebd73-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="ebd73-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebd73-105">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ebd73-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ebd73-106">Attributes and Elements</span></span>

<span data-ttu-id="ebd73-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ebd73-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ebd73-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ebd73-108">Attributes</span></span>

|<span data-ttu-id="ebd73-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ebd73-109">Attribute</span></span>|<span data-ttu-id="ebd73-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebd73-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="ebd73-111">Çar</span><span class="sxs-lookup"><span data-stu-id="ebd73-111">factory</span></span>|<span data-ttu-id="ebd73-112">Bir hizmet etkinleştirme öğesi üreten fabrika 'nin CLR türü adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ebd73-112">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="ebd73-113">hizmet</span><span class="sxs-lookup"><span data-stu-id="ebd73-113">service</span></span>|<span data-ttu-id="ebd73-114">Hizmeti uygulayan ServiceType (tam nitelenmiş TypeName veya Short TypeName (App_Code klasörüne yerleştirildiğinde).</span><span class="sxs-lookup"><span data-stu-id="ebd73-114">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="ebd73-115">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="ebd73-115">relativeAddress</span></span>|<span data-ttu-id="ebd73-116">Geçerli IIS uygulamasındaki göreli adres (örneğin, "Service. svc").</span><span class="sxs-lookup"><span data-stu-id="ebd73-116">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="ebd73-117">WCF 4,0 ' de, bu göreli adresin bilinen dosya uzantılarından birini (. svc,. xamlx,...) içermesi gerekir. RelativeUrl 'Si için fiziksel dosya yok</span><span class="sxs-lookup"><span data-stu-id="ebd73-117">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ebd73-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ebd73-118">Child Elements</span></span>

<span data-ttu-id="ebd73-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="ebd73-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ebd73-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ebd73-120">Parent Elements</span></span>

|<span data-ttu-id="ebd73-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ebd73-121">Element</span></span>|<span data-ttu-id="ebd73-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebd73-122">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="ebd73-123">Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="ebd73-123">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ebd73-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebd73-124">Remarks</span></span>

<span data-ttu-id="ebd73-125">Aşağıdaki örnek, Web. config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ebd73-125">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="ebd73-126">Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebd73-126">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="ebd73-127">Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ebd73-127">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="ebd73-128">`web.config`Yapılandırma içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebd73-128">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="ebd73-129">Ayrıca, `serviceHostingEnvironment` bir machineToApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="ebd73-129">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="ebd73-130">Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="ebd73-130">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="ebd73-131">Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="ebd73-131">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="ebd73-132">RelativeAddress, yani. svc,. xoml veya. xamlx için Uzantılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ebd73-132">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="ebd73-133">Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebd73-133">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="ebd73-134">Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ebd73-134">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebd73-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebd73-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
