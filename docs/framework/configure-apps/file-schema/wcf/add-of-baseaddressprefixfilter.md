---
title: <add> / <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 809e6d5504b56f86eb09a5d57931f922e1c18348
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973818"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="989fe-102">\<\<baseAddressPrefixFilter > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="989fe-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="989fe-103">IIS 'de bir Windows Communication Foundation (WCF) uygulaması barındırırken uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlayan doğrudan geçiş filtresini belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="989fe-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
<span data-ttu-id="989fe-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="989fe-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="989fe-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="989fe-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="989fe-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="989fe-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="989fe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<baseAddressPrefixFilters >** ](baseaddressprefixfilters.md)</span><span class="sxs-lookup"><span data-stu-id="989fe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)</span></span>\
<span data-ttu-id="989fe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="989fe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="989fe-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="989fe-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="989fe-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="989fe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="989fe-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="989fe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="989fe-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="989fe-112">Attributes</span></span>  
  
|<span data-ttu-id="989fe-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="989fe-113">Attribute</span></span>|<span data-ttu-id="989fe-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="989fe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="989fe-115">koy</span><span class="sxs-lookup"><span data-stu-id="989fe-115">prefix</span></span>|<span data-ttu-id="989fe-116">Temel adresin bir bölümünü eşleştirmek için kullanılan bir URI.</span><span class="sxs-lookup"><span data-stu-id="989fe-116">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="989fe-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="989fe-117">Child Elements</span></span>  
 <span data-ttu-id="989fe-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="989fe-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="989fe-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="989fe-119">Parent Elements</span></span>  
  
|<span data-ttu-id="989fe-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="989fe-120">Element</span></span>|<span data-ttu-id="989fe-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="989fe-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="989fe-122">baseAddressPrefixFilters > \<</span><span class="sxs-lookup"><span data-stu-id="989fe-122">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="989fe-123">IIS 'de bir Windows Communication Foundation (WCF) uygulaması barındırırken uygun IIS bağlamalarını seçme mekanizması sağlayan doğrudan geçiş filtrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="989fe-123">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="989fe-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="989fe-124">Remarks</span></span>  
 <span data-ttu-id="989fe-125">Önek filtresi, paylaşılan barındırma sağlayıcılarının, hizmet tarafından hangi URI 'Lerin kullanılacağını belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="989fe-125">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="989fe-126">Paylaşılan ana bilgisayarların aynı sitede aynı düzen için farklı temel adreslere sahip birden çok uygulamayı barındırmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="989fe-126">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="989fe-127">IIS Web siteleri, sanal dizinler içeren sanal uygulamalara yönelik kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="989fe-127">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="989fe-128">Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="989fe-128">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="989fe-129">IIS bağlamaları iki adet bilgi sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="989fe-129">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="989fe-130">Bağlama Protokolü (örneğin, HTTP), iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, hostheader) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="989fe-130">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="989fe-131">IIS, her bir site için birden çok IIS bağlaması belirtmeyi destekler ve bu, her bir şema için birden çok temel adrese neden</span><span class="sxs-lookup"><span data-stu-id="989fe-131">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="989fe-132">Bir site altında barındırılan bir WCF hizmeti her bir şema için yalnızca bir temel adrese bağlamaya izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtresi özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="989fe-132">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="989fe-133">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek listesi filtresine göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="989fe-133">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="989fe-134">Örneğin, siteniz aşağıdaki temel adresleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="989fe-134">For example, your site can contain the following base addresses:</span></span>
  
``` 
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="989fe-135">Uygulama etki alanı düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="989fe-135">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="989fe-136">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000`, kendisine geçirilmesine izin verilen kendi şemaları için tek temel adreslerdir.</span><span class="sxs-lookup"><span data-stu-id="989fe-136">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="989fe-137">Varsayılan olarak, ön ek belirtilmediğinde tüm adresler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="989fe-137">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="989fe-138">Ön eki belirtmek yalnızca ilgili düzenin eşleşen temel adresinin geçirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="989fe-138">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="989fe-139">Filtre herhangi bir joker karakteri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="989fe-139">The filter does not support any wildcards.</span></span> <span data-ttu-id="989fe-140">Ayrıca, IIS tarafından sağlanan baseAddresses, `baseAddressPrefixFilters` listesinde bulunmayan diğer şemalara ait adreslere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="989fe-140">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="989fe-141">Bu adresler filtrelenmez.</span><span class="sxs-lookup"><span data-stu-id="989fe-141">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="989fe-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="989fe-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="989fe-143">Barındırma</span><span class="sxs-lookup"><span data-stu-id="989fe-143">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
