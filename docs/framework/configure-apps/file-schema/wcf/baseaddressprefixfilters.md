---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: ce224a2a1d6d96f2bc72e9291e7256d264d86d50
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149033"
---
# \<baseAddressPrefixFilters>

<span data-ttu-id="25f94-101">IIS 'de Windows Communication Foundation (WCF) uygulamasını barındırırken uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlayan geçiş filtrelerini belirten yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="25f94-101">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="25f94-102">\<baseAddressPrefixFilters> "localhost" öğesini tanımıyor; Bunun yerine tam makine adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="25f94-102">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**  
  
## <a name="syntax"></a><span data-ttu-id="25f94-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="25f94-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25f94-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25f94-104">Attributes and Elements</span></span>  

 <span data-ttu-id="25f94-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25f94-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25f94-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25f94-106">Attributes</span></span>  

 <span data-ttu-id="25f94-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="25f94-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25f94-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25f94-108">Child Elements</span></span>  
  
|<span data-ttu-id="25f94-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="25f94-109">Element</span></span>|<span data-ttu-id="25f94-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25f94-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="25f94-111">Hizmet ana bilgisayarı tarafından kullanılan taban adresler için önek filtresini belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="25f94-111">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25f94-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25f94-112">Parent Elements</span></span>  
  
|<span data-ttu-id="25f94-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="25f94-113">Element</span></span>|<span data-ttu-id="25f94-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25f94-114">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="25f94-115">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25f94-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25f94-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25f94-116">Remarks</span></span>  

 <span data-ttu-id="25f94-117">Önek filtresi, paylaşılan barındırma sağlayıcılarının, hizmet tarafından hangi URI 'Lerin kullanılacağını belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="25f94-117">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="25f94-118">Paylaşılan ana bilgisayarların aynı sitede aynı düzen için farklı temel adreslere sahip birden çok uygulamayı barındırmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="25f94-118">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="25f94-119">IIS Web siteleri, sanal dizinler içeren sanal uygulamalara yönelik kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="25f94-119">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="25f94-120">Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="25f94-120">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="25f94-121">IIS bağlamaları iki adet bilgi sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="25f94-121">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="25f94-122">Bağlama Protokolü (örneğin, HTTP), iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, hostheader) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="25f94-122">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="25f94-123">IIS, her bir site için birden çok IIS bağlaması belirtmeyi destekler ve bu, her bir şema için birden çok temel adrese neden</span><span class="sxs-lookup"><span data-stu-id="25f94-123">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="25f94-124">Bir site altında barındırılan bir WCF hizmeti her bir şema için yalnızca bir temel adrese bağlamaya izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtresi özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25f94-124">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="25f94-125">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek listesi filtresine göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="25f94-125">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="25f94-126">Örneğin, siteniz aşağıdaki temel adresleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="25f94-126">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="25f94-127">Uygulama etki alanı düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25f94-127">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="25f94-128">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` kendisine geçirilmesine izin verilen kendi şemaları için tek temel adreslerdir.</span><span class="sxs-lookup"><span data-stu-id="25f94-128">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="25f94-129">Varsayılan olarak, ön ek belirtilmediğinde tüm adresler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="25f94-129">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="25f94-130">Ön eki belirtmek yalnızca ilgili düzenin eşleşen temel adresinin geçirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="25f94-130">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25f94-131">Filtre herhangi bir joker karakteri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="25f94-131">The filter does not support any wildcards.</span></span> <span data-ttu-id="25f94-132">Buna ek olarak, IIS tarafından sağlanan baseAddresses, listede bulunmayan diğer şemalara göre adreslere sahip olabilir `baseAddressPrefixFilters` .</span><span class="sxs-lookup"><span data-stu-id="25f94-132">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="25f94-133">Bu adresler filtrelenmez.</span><span class="sxs-lookup"><span data-stu-id="25f94-133">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f94-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25f94-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="25f94-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="25f94-135">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
