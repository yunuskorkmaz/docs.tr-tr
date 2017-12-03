---
title: '&lt;baseAddressPrefixFilter&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd0a0d7fc5a83c78a56df796714e70e2e2a61767
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a><span data-ttu-id="fb2f4-102">&lt;baseAddressPrefixFilter&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="fb2f4-102">&lt;add&gt; of &lt;baseAddressPrefixFilter&gt;</span></span>
<span data-ttu-id="fb2f4-103">Uygun Internet Information Services (IIS) bağları barındırırken seçmek için bir mekanizma sağlar bir geçiş filtre belirten bir yapılandırma öğesi temsil eden bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] IIS'de uygulama.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application in IIS.</span></span>  
  
 <span data-ttu-id="fb2f4-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fb2f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fb2f4-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="fb2f4-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="fb2f4-106">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="fb2f4-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="fb2f4-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="fb2f4-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2f4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb2f4-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb2f4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb2f4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fb2f4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb2f4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb2f4-111">Attributes</span></span>  
  
|<span data-ttu-id="fb2f4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fb2f4-112">Attribute</span></span>|<span data-ttu-id="fb2f4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb2f4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb2f4-114">önek</span><span class="sxs-lookup"><span data-stu-id="fb2f4-114">prefix</span></span>|<span data-ttu-id="fb2f4-115">Temel adres kısmen eşleştirmek için kullanılan bir URI.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb2f4-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb2f4-116">Child Elements</span></span>  
 <span data-ttu-id="fb2f4-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb2f4-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb2f4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fb2f4-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb2f4-119">Element</span></span>|<span data-ttu-id="fb2f4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb2f4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb2f4-121">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="fb2f4-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="fb2f4-122">Uygun IIS bağları barındırırken seçmek için bir mekanizma sağlar geçiş filtrelerini belirtme yapılandırma öğeleri koleksiyonu bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] IIS'de uygulama.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb2f4-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb2f4-123">Remarks</span></span>  
 <span data-ttu-id="fb2f4-124">Bir önek filtre, hangi URI'ler olan hizmet tarafından kullanılmak üzere belirtmek paylaşılan barındırma hizmeti sağlayıcıları için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="fb2f4-125">Birden çok uygulama aynı sitedeki aynı düzeni için farklı temel adresleriyle barındırmak paylaşılan konakları sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="fb2f4-126">IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="fb2f4-127">Uygulama bir sitedeki bir veya daha fazla IIS bağlama aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="fb2f4-128">IIS bağlamaları iki parça bilgi sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="fb2f4-129">Bağlama Protokolü (örneğin, HTTP) üzerinden iletişimin şeması tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, AnaBilgisayarÜstbilgisi) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="fb2f4-130">IIS, her şeması için birden çok taban adresi sonuçlanan her site için birden çok IIS bağlamaları belirtmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="fb2f4-131">Çünkü bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir site altında barındırılan hizmet sağlayan her şeması için yalnızca bir temel adres için bağlama, barındırılan hizmet gerekli temel adresini seçmek için önek filtre özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-131">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="fb2f4-132">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek liste filtresi göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="fb2f4-133">Örneğin, siteniz aşağıdaki temel adresler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="fb2f4-134">Uygulama etki alanı düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="fb2f4-135">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` üzerinden iletilecek izin kendi ilgili şemaları için yalnızca temel adresleridir.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="fb2f4-136">Önek belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="fb2f4-137">Önek belirtme yalnızca eşleşen taban adresi üzerinden iletilecek Bu plan için izin verir.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb2f4-138">Filtre herhangi joker karakterleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="fb2f4-139">Ayrıca, IIS tarafından sağlanan baseAddresses adresleri değil diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="fb2f4-140">Bu adresler filtrelendi değil.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2f4-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb2f4-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="fb2f4-142">Barındırma</span><span class="sxs-lookup"><span data-stu-id="fb2f4-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
