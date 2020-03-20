---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 0673507b72690c3a5c7dcc35442c05e378dba43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153041"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="cf936-101">\<baseAddressPrefixFiltreler></span><span class="sxs-lookup"><span data-stu-id="cf936-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="cf936-102">IIS'de Windows Communication Foundation (WCF) uygulamasını barındırırken uygun Internet Bilgi Hizmetleri (IIS) bağlaçlarını seçmek için bir mekanizma sağlayan filtrelerden geçiş belirten yapılandırma öğeleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf936-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="cf936-103">\<baseAddressPrefixFilters> "localhost"u tanımıyor; bunun yerine tam nitelikli makine adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="cf936-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
<span data-ttu-id="cf936-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf936-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf936-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cf936-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cf936-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingÇevre>**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="cf936-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="cf936-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFiltreler>**</span><span class="sxs-lookup"><span data-stu-id="cf936-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf936-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf936-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf936-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf936-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cf936-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf936-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf936-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cf936-111">Attributes</span></span>  
 <span data-ttu-id="cf936-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="cf936-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf936-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf936-113">Child Elements</span></span>  
  
|<span data-ttu-id="cf936-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="cf936-114">Element</span></span>|<span data-ttu-id="cf936-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf936-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf936-116">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="cf936-116">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="cf936-117">Hizmet ana bilgisayarı tarafından kullanılan temel adresler için önek filtresi belirten bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="cf936-117">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf936-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf936-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cf936-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="cf936-119">Element</span></span>|<span data-ttu-id="cf936-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf936-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf936-121">\<serviceHostingÇevre></span><span class="sxs-lookup"><span data-stu-id="cf936-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="cf936-122">Hizmet barındırma ortamının belirli bir aktarım için anlık olarak çalıştığı türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cf936-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf936-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf936-123">Remarks</span></span>  
 <span data-ttu-id="cf936-124">Önek filtresi, paylaşılan barındırma sağlayıcılarının hizmet tarafından hangi URL'lerin kullanılacağını belirtmelerine yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf936-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="cf936-125">Paylaşılan ana bilgisayarların aynı sitede aynı şemaya yönelik farklı temel adreslere sahip birden çok uygulamayı barındırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf936-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="cf936-126">IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="cf936-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="cf936-127">Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf936-127">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="cf936-128">IIS ciltlemeleri iki bilgi parçası sağlar: bağlama protokolü ve bağlayıcı bilgiler.</span><span class="sxs-lookup"><span data-stu-id="cf936-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="cf936-129">Bağlama protokolü (örneğin, HTTP) iletişimin gerçekleştiği düzeni tanımlar ve bağlayıcı bilgiler (örneğin, IP Adresi, Bağlantı Noktası, Ana Bilgisayar) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="cf936-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="cf936-130">IIS, her site için birden çok IIS bağlayıcısı belirtmeyi destekler ve bu da her düzen için birden çok temel adresle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cf936-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="cf936-131">Bir site altında barındırılan bir WCF hizmeti, her düzen için yalnızca bir temel adrese bağlamaya izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtresi özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf936-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="cf936-132">IIS tarafından sağlanan gelen temel adresler isteğe bağlı öneek listesi filtresine göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="cf936-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="cf936-133">Örneğin, siteniz aşağıdaki temel adresleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="cf936-133">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="cf936-134">Appdomain düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf936-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="cf936-135">Bu örnekte `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` ve kendi şemaları için geçirilen izin verilen tek temel adresleri vardır.</span><span class="sxs-lookup"><span data-stu-id="cf936-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="cf936-136">Varsayılan olarak, önek belirtilmediğinde, tüm adresler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cf936-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="cf936-137">Önek belirtilmesi yalnızca bu düzenin eşleşen temel adresinin geçirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="cf936-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf936-138">Filtre herhangi bir joker karakter desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cf936-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="cf936-139">Ayrıca, IIS tarafından sağlanan temel Adresler `baseAddressPrefixFilters` listede bulunmayan diğer düzenlere bağlı adreslere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf936-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="cf936-140">Bu adresler filtreuygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="cf936-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf936-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf936-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="cf936-142">Barındırma</span><span class="sxs-lookup"><span data-stu-id="cf936-142">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
