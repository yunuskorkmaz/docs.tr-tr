---
title: '&lt;serviceActivations&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: b40127d531926f103f3e367c8721e8f5ff8e1a99
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151546"
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="2064e-102">&lt;serviceActivations&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="2064e-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="2064e-103">Windows Communication Foundation (WCF) hizmet türlerinizi eşleştiren sanal hizmet aktivasyon ayarlarını tanımlamanıza olanak sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="2064e-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="2064e-104">Bu WAS içinde barındırılan hizmetleri etkinleştirmeniz mümkün kılar / IIS .svc dosyası olmadan.</span><span class="sxs-lookup"><span data-stu-id="2064e-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="2064e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2064e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2064e-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="2064e-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2064e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2064e-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2064e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2064e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2064e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2064e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2064e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2064e-110">Attributes</span></span>  
  
|<span data-ttu-id="2064e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2064e-111">Attribute</span></span>|<span data-ttu-id="2064e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2064e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2064e-113">Fabrika</span><span class="sxs-lookup"><span data-stu-id="2064e-113">factory</span></span>|<span data-ttu-id="2064e-114">Bir hizmet aktivasyon öğesini üreten üretici CLR tür adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="2064e-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="2064e-115">hizmet</span><span class="sxs-lookup"><span data-stu-id="2064e-115">service</span></span>|<span data-ttu-id="2064e-116">(Tam nitelikli tür adı veya kısa Typename (App_Code klasörü içinde yerleştirilir olduğunda). hizmeti uygulayan ServiceType</span><span class="sxs-lookup"><span data-stu-id="2064e-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="2064e-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="2064e-117">relativeAddress</span></span>|<span data-ttu-id="2064e-118">Geçerli bir IIS uygulama - örneğin "Service.svc" içinde göreli adresi.</span><span class="sxs-lookup"><span data-stu-id="2064e-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="2064e-119">WCF 4. 0'göreli bu adresi bir bilinen dosya uzantıları (.svc .xamlx,...) içeren var. Fiziksel dosya için relativeUrl var olması</span><span class="sxs-lookup"><span data-stu-id="2064e-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2064e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2064e-120">Child Elements</span></span>  
 <span data-ttu-id="2064e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="2064e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2064e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2064e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2064e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="2064e-123">Element</span></span>|<span data-ttu-id="2064e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2064e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2064e-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="2064e-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="2064e-126">Aktivasyon ayarlarını tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="2064e-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2064e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2064e-127">Remarks</span></span>  
 <span data-ttu-id="2064e-128">Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2064e-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="2064e-129">Bu yapılandırmayı kullanarak .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2064e-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="2064e-130">Unutmayın `<serviceHostingEnvironment>` uygulama düzeyinde yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="2064e-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="2064e-131">Yerleştirmek sahip olduğunuz `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren.</span><span class="sxs-lookup"><span data-stu-id="2064e-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="2064e-132">Ayrıca, `serviceHostingEnvironment` machinetoApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="2064e-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="2064e-133">Tek bir hizmette makine kökündeki kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.</span><span class="sxs-lookup"><span data-stu-id="2064e-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="2064e-134">Yapılandırma temelli etkinleştirme, etkinleştirme hem http hem de olmayan http protokolü üzerinden destekler.</span><span class="sxs-lookup"><span data-stu-id="2064e-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="2064e-135">Yani .svc, .xoml veya .xamlx relatativeAddress uzantılarında gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="2064e-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="2064e-136">Sonra hizmeti uzantıyı etkinleştirmek üzere olanak sağlayacak bilinen buildProviders kendi uzantılarınızı eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2064e-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="2064e-137">Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2064e-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2064e-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2064e-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
