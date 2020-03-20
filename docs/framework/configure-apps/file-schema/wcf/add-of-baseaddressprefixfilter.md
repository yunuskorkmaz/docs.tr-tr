---
title: <add> / <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 8fdae02b558708a9b3f4535123752dce12dd5cf5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153146"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="97a39-102">\<\<baseAddressPrefixFilter>> ekleyin</span><span class="sxs-lookup"><span data-stu-id="97a39-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="97a39-103">IIS'de bir Windows Communication Foundation (WCF) uygulamasını barındırırken uygun Internet Bilgi Hizmetleri (IIS) bağlaçlarını seçmek için bir mekanizma sağlayan bir geçiş filtresi belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="97a39-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
<span data-ttu-id="97a39-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="97a39-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="97a39-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="97a39-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="97a39-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingÇevre>**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="97a39-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="97a39-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFiltreler>**](baseaddressprefixfilters.md)</span><span class="sxs-lookup"><span data-stu-id="97a39-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)</span></span>\
<span data-ttu-id="97a39-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="97a39-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97a39-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97a39-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97a39-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="97a39-110">Attributes and Elements</span></span>  
 <span data-ttu-id="97a39-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97a39-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97a39-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="97a39-112">Attributes</span></span>  
  
|<span data-ttu-id="97a39-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="97a39-113">Attribute</span></span>|<span data-ttu-id="97a39-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97a39-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97a39-115">Önek</span><span class="sxs-lookup"><span data-stu-id="97a39-115">prefix</span></span>|<span data-ttu-id="97a39-116">Temel adresin bir bölümüyle eşleşecek şekilde kullanılan BIR URI.</span><span class="sxs-lookup"><span data-stu-id="97a39-116">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97a39-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="97a39-117">Child Elements</span></span>  
 <span data-ttu-id="97a39-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="97a39-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97a39-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="97a39-119">Parent Elements</span></span>  
  
|<span data-ttu-id="97a39-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="97a39-120">Element</span></span>|<span data-ttu-id="97a39-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97a39-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97a39-122">\<baseAddressPrefixFiltreler></span><span class="sxs-lookup"><span data-stu-id="97a39-122">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="97a39-123">IIS'de bir Windows Communication Foundation (WCF) uygulamasını barındırırken uygun IIS bağlamalarını seçmek için bir mekanizma sağlayan geçiş filtrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="97a39-123">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97a39-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97a39-124">Remarks</span></span>  
 <span data-ttu-id="97a39-125">Önek filtresi, paylaşılan barındırma sağlayıcılarının hizmet tarafından hangi URL'lerin kullanılacağını belirtmelerine yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="97a39-125">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="97a39-126">Paylaşılan ana bilgisayarların aynı sitede aynı şemaya yönelik farklı temel adreslere sahip birden çok uygulamayı barındırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="97a39-126">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="97a39-127">IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="97a39-127">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="97a39-128">Bir sitedeki uygulamaya bir veya daha fazla IIS bağlama yoluyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="97a39-128">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="97a39-129">IIS ciltlemeleri iki bilgi parçası sağlar: bağlama protokolü ve bağlayıcı bilgiler.</span><span class="sxs-lookup"><span data-stu-id="97a39-129">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="97a39-130">Bağlama protokolü (örneğin, HTTP) iletişimin gerçekleştiği düzeni tanımlar ve bağlayıcı bilgiler (örneğin, IP Adresi, Bağlantı Noktası, Ana Bilgisayar) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="97a39-130">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="97a39-131">IIS, her site için birden çok IIS bağlayıcısı belirtmeyi destekler ve bu da her düzen için birden çok temel adresle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="97a39-131">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="97a39-132">Bir site altında barındırılan bir WCF hizmeti, her düzen için yalnızca bir temel adrese bağlamaya izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtresi özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97a39-132">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="97a39-133">IIS tarafından sağlanan gelen temel adresler isteğe bağlı öneek listesi filtresine göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="97a39-133">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="97a39-134">Örneğin, siteniz aşağıdaki temel adresleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="97a39-134">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="97a39-135">Appdomain düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97a39-135">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="97a39-136">Bu örnekte `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` ve geçmesine izin verilen kendi düzenleri için tek temel adresleri vardır.</span><span class="sxs-lookup"><span data-stu-id="97a39-136">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="97a39-137">Varsayılan olarak, önek belirtilmediğinde, tüm adresler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="97a39-137">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="97a39-138">Önek belirtilmesi yalnızca bu düzenin eşleşen temel adresinin geçirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="97a39-138">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97a39-139">Filtre herhangi bir joker karakter desteklemez.</span><span class="sxs-lookup"><span data-stu-id="97a39-139">The filter does not support any wildcards.</span></span> <span data-ttu-id="97a39-140">Ayrıca, IIS tarafından sağlanan temel Adresler `baseAddressPrefixFilters` listede bulunmayan diğer düzenlere bağlı adreslere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="97a39-140">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="97a39-141">Bu adresler filtreuygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="97a39-141">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a39-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97a39-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="97a39-143">Barındırma</span><span class="sxs-lookup"><span data-stu-id="97a39-143">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
