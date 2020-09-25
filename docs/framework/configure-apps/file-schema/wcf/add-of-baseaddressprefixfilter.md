---
title: <add> / <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: fefe85381aec113da123e6f2246aee340b0cf97a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181602"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="c8a2e-102">\<add> / \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="c8a2e-102">\<add> of \<baseAddressPrefixFilter></span></span>

<span data-ttu-id="c8a2e-103">IIS 'de bir Windows Communication Foundation (WCF) uygulaması barındırırken uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlayan doğrudan geçiş filtresini belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c8a2e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8a2e-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8a2e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c8a2e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c8a2e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8a2e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c8a2e-107">Attributes</span></span>  
  
|<span data-ttu-id="c8a2e-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c8a2e-108">Attribute</span></span>|<span data-ttu-id="c8a2e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8a2e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8a2e-110">koy</span><span class="sxs-lookup"><span data-stu-id="c8a2e-110">prefix</span></span>|<span data-ttu-id="c8a2e-111">Temel adresin bir bölümünü eşleştirmek için kullanılan bir URI.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-111">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8a2e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c8a2e-112">Child Elements</span></span>  

 <span data-ttu-id="c8a2e-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8a2e-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c8a2e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c8a2e-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="c8a2e-115">Element</span></span>|<span data-ttu-id="c8a2e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8a2e-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="c8a2e-117">IIS 'de bir Windows Communication Foundation (WCF) uygulaması barındırırken uygun IIS bağlamalarını seçme mekanizması sağlayan doğrudan geçiş filtrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-117">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8a2e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8a2e-118">Remarks</span></span>  

 <span data-ttu-id="c8a2e-119">Önek filtresi, paylaşılan barındırma sağlayıcılarının, hizmet tarafından hangi URI 'Lerin kullanılacağını belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-119">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="c8a2e-120">Paylaşılan ana bilgisayarların aynı sitede aynı düzen için farklı temel adreslere sahip birden çok uygulamayı barındırmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-120">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="c8a2e-121">IIS Web siteleri, sanal dizinler içeren sanal uygulamalara yönelik kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-121">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="c8a2e-122">Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-122">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="c8a2e-123">IIS bağlamaları iki adet bilgi sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-123">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="c8a2e-124">Bağlama Protokolü (örneğin, HTTP), iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, hostheader) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-124">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="c8a2e-125">IIS, her bir site için birden çok IIS bağlaması belirtmeyi destekler ve bu, her bir şema için birden çok temel adrese neden</span><span class="sxs-lookup"><span data-stu-id="c8a2e-125">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="c8a2e-126">Bir site altında barındırılan bir WCF hizmeti her bir şema için yalnızca bir temel adrese bağlamaya izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtresi özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-126">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="c8a2e-127">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek listesi filtresine göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-127">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="c8a2e-128">Örneğin, siteniz aşağıdaki temel adresleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="c8a2e-128">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="c8a2e-129">Uygulama etki alanı düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-129">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="c8a2e-130">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` kendisine geçirilmesine izin verilen kendi şemaları için tek temel adreslerdir.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-130">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="c8a2e-131">Varsayılan olarak, ön ek belirtilmediğinde tüm adresler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-131">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="c8a2e-132">Ön eki belirtmek yalnızca ilgili düzenin eşleşen temel adresinin geçirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-132">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8a2e-133">Filtre herhangi bir joker karakteri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-133">The filter does not support any wildcards.</span></span> <span data-ttu-id="c8a2e-134">Buna ek olarak, IIS tarafından sağlanan baseAddresses, listede bulunmayan diğer şemalara göre adreslere sahip olabilir `baseAddressPrefixFilters` .</span><span class="sxs-lookup"><span data-stu-id="c8a2e-134">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="c8a2e-135">Bu adresler filtrelenmez.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-135">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a2e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8a2e-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="c8a2e-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="c8a2e-137">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
