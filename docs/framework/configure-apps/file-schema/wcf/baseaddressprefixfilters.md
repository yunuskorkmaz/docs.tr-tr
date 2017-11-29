---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 653f2e48e8743cd07fe0e8a9adb92eb5691049f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="e26f9-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="e26f9-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="e26f9-103">Yapılandırma öğesi uygun Internet Information Services (IIS) bağları barındırırken seçmek için bir mekanizma sağlar filtrelerden geçişi belirten bir koleksiyonunu temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] IIS'de uygulama.</span><span class="sxs-lookup"><span data-stu-id="e26f9-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="e26f9-104">\<baseAddressPrefixFilters > yok "localhost" tanımak, bunun yerine tam makine adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e26f9-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="e26f9-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e26f9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e26f9-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="e26f9-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e26f9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e26f9-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e26f9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e26f9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e26f9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e26f9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e26f9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e26f9-110">Attributes</span></span>  
 <span data-ttu-id="e26f9-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="e26f9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e26f9-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e26f9-112">Child Elements</span></span>  
  
|<span data-ttu-id="e26f9-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="e26f9-113">Element</span></span>|<span data-ttu-id="e26f9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e26f9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e26f9-115">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="e26f9-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="e26f9-116">Hizmet ana bilgisayar tarafından kullanılan temel adres için bir önek filtre belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="e26f9-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e26f9-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e26f9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e26f9-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e26f9-118">Element</span></span>|<span data-ttu-id="e26f9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e26f9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e26f9-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="e26f9-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="e26f9-121">Belirli bir barındırma ortamı hizmeti başlatır türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e26f9-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e26f9-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e26f9-122">Remarks</span></span>  
 <span data-ttu-id="e26f9-123">Bir önek filtre, hangi URI'ler olan hizmet tarafından kullanılmak üzere belirtmek paylaşılan barındırma hizmeti sağlayıcıları için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e26f9-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="e26f9-124">Birden çok uygulama aynı sitedeki aynı düzeni için farklı temel adresleriyle barındırmak paylaşılan konakları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e26f9-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="e26f9-125">IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="e26f9-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="e26f9-126">Uygulama bir sitedeki bir veya daha fazla IIS bağlamaları erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e26f9-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="e26f9-127">IIS bağlamaları iki parça bilgi sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e26f9-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="e26f9-128">Bağlama Protokolü (örneğin, HTTP) üzerinden iletişimin şeması tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, AnaBilgisayarÜstbilgisi) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="e26f9-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="e26f9-129">IIS, her şeması için birden çok taban adresi sonuçlanan her site için birden çok IIS bağlamaları belirtmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="e26f9-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="e26f9-130">Çünkü bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir site altında barındırılan hizmet sağlayan her şeması için yalnızca bir temel adres için bağlama, barındırılan hizmet gerekli temel adresini seçmek için önek filtre özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e26f9-130">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="e26f9-131">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek liste filtresi göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="e26f9-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="e26f9-132">Örneğin, siteniz aşağıdaki temel adresler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e26f9-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="e26f9-133">Uygulama etki alanı düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e26f9-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="e26f9-134">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` üzerinden iletilecek izin kendi ilgili şemaları için yalnızca temel adresleridir.</span><span class="sxs-lookup"><span data-stu-id="e26f9-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="e26f9-135">Önek belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e26f9-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="e26f9-136">Önek belirtme yalnızca eşleşen taban adresi üzerinden iletilecek Bu plan için izin verir.</span><span class="sxs-lookup"><span data-stu-id="e26f9-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e26f9-137">Filtre herhangi joker karakterleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e26f9-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="e26f9-138">Ayrıca, IIS tarafından sağlanan baseAddresses adresleri değil diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi.</span><span class="sxs-lookup"><span data-stu-id="e26f9-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="e26f9-139">Bu adresler filtrelendi değil.</span><span class="sxs-lookup"><span data-stu-id="e26f9-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e26f9-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e26f9-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="e26f9-141">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e26f9-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
