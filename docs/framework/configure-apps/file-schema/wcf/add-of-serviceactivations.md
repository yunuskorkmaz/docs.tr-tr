---
title: '&lt;serviceActivations&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c49845169265e48b232963ed5a2e6215be75d3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="d15a1-102">&lt;serviceActivations&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="d15a1-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="d15a1-103">Eşlenen sanal hizmeti etkinleştirme ayarlarını tanımlamanızı sağlar bir yapılandırma öğesi, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet türleri.</span><span class="sxs-lookup"><span data-stu-id="d15a1-103">A configuration element that allows you to define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="d15a1-104">Bu WAS içinde barındırılan hizmetlere etkinleştirmek mümkün kılar / IIS .svc dosyası olmadan.</span><span class="sxs-lookup"><span data-stu-id="d15a1-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="d15a1-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d15a1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d15a1-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="d15a1-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d15a1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d15a1-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d15a1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d15a1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d15a1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d15a1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d15a1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d15a1-110">Attributes</span></span>  
  
|<span data-ttu-id="d15a1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d15a1-111">Attribute</span></span>|<span data-ttu-id="d15a1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d15a1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d15a1-113">Fabrika</span><span class="sxs-lookup"><span data-stu-id="d15a1-113">factory</span></span>|<span data-ttu-id="d15a1-114">Hizmeti etkinleştirme öğesi oluşturur Fabrika CLR türü adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="d15a1-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="d15a1-115">hizmet</span><span class="sxs-lookup"><span data-stu-id="d15a1-115">service</span></span>|<span data-ttu-id="d15a1-116">(Tam nitelikli Typename veya (App_Code klasörüne yerleştirilir olduğunda) kısa Typename. hizmeti uygulayan ServiceType</span><span class="sxs-lookup"><span data-stu-id="d15a1-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="d15a1-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="d15a1-117">relativeAddress</span></span>|<span data-ttu-id="d15a1-118">Geçerli bir IIS uygulama - örneğin "Service.svc" içinde göreli adresi.</span><span class="sxs-lookup"><span data-stu-id="d15a1-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="d15a1-119">WCF 4. 0'göreli bu adresi bir bilinen dosya uzantılarını (.svc, .xamlx,...) içermesi gerekir. Fiziksel dosya için relativeUrl varolmak zorunda</span><span class="sxs-lookup"><span data-stu-id="d15a1-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d15a1-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d15a1-120">Child Elements</span></span>  
 <span data-ttu-id="d15a1-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="d15a1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d15a1-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d15a1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d15a1-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="d15a1-123">Element</span></span>|<span data-ttu-id="d15a1-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d15a1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d15a1-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="d15a1-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="d15a1-126">Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="d15a1-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d15a1-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d15a1-127">Remarks</span></span>  
 <span data-ttu-id="d15a1-128">Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d15a1-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d15a1-129">Bu yapılandırmayı kullanarak, bir .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d15a1-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="d15a1-130">Unutmayın `<serviceHostingEnvironment>` uygulama düzeyi yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="d15a1-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="d15a1-131">Yerleştirmek zorunda `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren.</span><span class="sxs-lookup"><span data-stu-id="d15a1-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="d15a1-132">Ayrıca, `serviceHostingEnvironment` machinetoApplication devralınabilir bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="d15a1-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="d15a1-133">Tek bir hizmeti makinenin kök dizininde kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.</span><span class="sxs-lookup"><span data-stu-id="d15a1-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="d15a1-134">Yapılandırma temelli etkinleştirme hem http hem de http olmayan protokolü üzerinden etkinleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="d15a1-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="d15a1-135">Yani .svc, .xoml veya .xamlx relatativeAddress uzantılarında gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d15a1-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="d15a1-136">Ardından, uzantıyı hizmeti etkinleştirmek üzere olanak tanır bilinen buildProviders kendi uzantıları eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d15a1-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="d15a1-137">Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtlar geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d15a1-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d15a1-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d15a1-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
