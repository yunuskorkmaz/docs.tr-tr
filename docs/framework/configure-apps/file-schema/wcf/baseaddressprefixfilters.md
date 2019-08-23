---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 8a59f651318e18411b1485fc4eebeb7a550afca0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919849"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="04b16-101">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="04b16-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="04b16-102">IIS 'de Windows Communication Foundation (WCF) uygulamasını barındırırken uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlayan geçiş filtrelerini belirten yapılandırma öğelerinin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="04b16-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="04b16-103">\<baseAddressPrefixFilters > "localhost" öğesini tanımıyor, bunun yerine tam makine adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="04b16-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="04b16-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="04b16-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="04b16-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="04b16-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04b16-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04b16-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04b16-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="04b16-107">Attributes and Elements</span></span>  
 <span data-ttu-id="04b16-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="04b16-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04b16-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="04b16-109">Attributes</span></span>  
 <span data-ttu-id="04b16-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="04b16-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04b16-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="04b16-111">Child Elements</span></span>  
  
|<span data-ttu-id="04b16-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="04b16-112">Element</span></span>|<span data-ttu-id="04b16-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04b16-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04b16-114">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="04b16-114">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="04b16-115">Hizmet ana bilgisayarı tarafından kullanılan taban adresler için önek filtresini belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="04b16-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04b16-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="04b16-116">Parent Elements</span></span>  
  
|<span data-ttu-id="04b16-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="04b16-117">Element</span></span>|<span data-ttu-id="04b16-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04b16-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04b16-119">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="04b16-119">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="04b16-120">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="04b16-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04b16-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04b16-121">Remarks</span></span>  
 <span data-ttu-id="04b16-122">Önek filtresi, paylaşılan barındırma sağlayıcılarının, hizmet tarafından hangi URI 'Lerin kullanılacağını belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="04b16-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="04b16-123">Paylaşılan ana bilgisayarların aynı sitede aynı düzen için farklı temel adreslere sahip birden çok uygulamayı barındırmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="04b16-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="04b16-124">IIS Web siteleri, sanal dizinler içeren sanal uygulamalara yönelik kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="04b16-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="04b16-125">Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="04b16-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="04b16-126">IIS bağlamaları iki adet bilgi sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="04b16-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="04b16-127">Bağlama Protokolü (örneğin, HTTP), iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, hostheader) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="04b16-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="04b16-128">IIS, her bir site için birden çok IIS bağlaması belirtmeyi destekler ve bu, her bir şema için birden çok temel adrese neden</span><span class="sxs-lookup"><span data-stu-id="04b16-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="04b16-129">Bir site altında barındırılan bir WCF hizmeti her bir şema için yalnızca bir temel adrese bağlamaya izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtresi özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04b16-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="04b16-130">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek listesi filtresine göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="04b16-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="04b16-131">Örneğin, siteniz aşağıdaki temel adresleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="04b16-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="04b16-132">Uygulama etki alanı düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04b16-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="04b16-133">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` kendisine geçirilmesine izin verilen kendi şemaları için tek temel adreslerdir.</span><span class="sxs-lookup"><span data-stu-id="04b16-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="04b16-134">Varsayılan olarak, ön ek belirtilmediğinde tüm adresler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="04b16-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="04b16-135">Ön eki belirtmek yalnızca ilgili düzenin eşleşen temel adresinin geçirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="04b16-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04b16-136">Filtre herhangi bir joker karakteri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="04b16-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="04b16-137">Buna ek olarak, IIS tarafından sağlanan BaseAddresses, `baseAddressPrefixFilters` listede bulunmayan diğer şemalara göre adreslere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="04b16-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="04b16-138">Bu adresler filtrelenmez.</span><span class="sxs-lookup"><span data-stu-id="04b16-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b16-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04b16-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="04b16-140">Barındırma</span><span class="sxs-lookup"><span data-stu-id="04b16-140">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
