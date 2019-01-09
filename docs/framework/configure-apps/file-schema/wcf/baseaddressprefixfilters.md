---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 04579980201b397e7ed92f55ffcb19e54de18aaa
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149234"
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="db243-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="db243-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="db243-103">IIS'de Windows Communication Foundation (WCF) uygulama uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlar filtreleri belirten geçişine yapılandırma koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db243-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="db243-104">\<baseAddressPrefixFilters > değil "localhost" olarak tanıyacak, bunun yerine tam makine adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="db243-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="db243-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="db243-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="db243-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="db243-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db243-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db243-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db243-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="db243-108">Attributes and Elements</span></span>  
 <span data-ttu-id="db243-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="db243-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db243-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="db243-110">Attributes</span></span>  
 <span data-ttu-id="db243-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="db243-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="db243-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="db243-112">Child Elements</span></span>  
  
|<span data-ttu-id="db243-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="db243-113">Element</span></span>|<span data-ttu-id="db243-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db243-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db243-115">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="db243-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="db243-116">Önek filtresi için hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="db243-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db243-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="db243-117">Parent Elements</span></span>  
  
|<span data-ttu-id="db243-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="db243-118">Element</span></span>|<span data-ttu-id="db243-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db243-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db243-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="db243-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="db243-121">Belirli bir hizmet barındırma ortamını gösteren türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="db243-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db243-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db243-122">Remarks</span></span>  
 <span data-ttu-id="db243-123">Önek filtresi, hangi bir URI'leri olan hizmet tarafından kullanılmak üzere belirtmek paylaşılan barındırma sağlayıcıları için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="db243-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="db243-124">Bu, birden çok uygulama ile aynı sitede aynı düzeni için farklı temel adresler barındırmak için paylaşılan ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="db243-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="db243-125">IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="db243-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="db243-126">Uygulama bir sitedeki bir veya daha fazla IIS bağlamaları erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="db243-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="db243-127">IIS bağlamaları, iki bilgi parçasını sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="db243-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="db243-128">İletişim oluştuğu Düzen Protokolü (örneğin, HTTP) bağlama tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, AnaBilgisayarÜstbilgisi) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="db243-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="db243-129">IIS, her şeması için birden çok taban adresi sonuçlanır her site için birden fazla IIS bağlamaları belirtme destekler.</span><span class="sxs-lookup"><span data-stu-id="db243-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="db243-130">Bir site altında barındırılan bir WCF hizmeti yalnızca bir temel adres bir bağlamayı her şeması için izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtreleme özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db243-130">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="db243-131">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı bir ön ek listesi filtre göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="db243-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="db243-132">Örneğin, siteniz aşağıdaki temel adresler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="db243-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="db243-133">Uygulama etki alanı düzeyinde bir önek filtre belirtmek için aşağıdaki yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db243-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="db243-134">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` aracılığıyla geçirilmesine izin verilir, kendi şemaları için yalnızca temel adresleridir.</span><span class="sxs-lookup"><span data-stu-id="db243-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="db243-135">Öneki belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="db243-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="db243-136">Önek belirleyerek eşleşen temel adresini doğrudan geçiş yapılacak bu şema için yalnızca sağlar.</span><span class="sxs-lookup"><span data-stu-id="db243-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db243-137">Filtre, herhangi bir joker karakterleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="db243-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="db243-138">Ayrıca, IIS tarafından sağlanan baseAddresses adresleri yok diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi.</span><span class="sxs-lookup"><span data-stu-id="db243-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="db243-139">Bu adresleri filtrelenir değil.</span><span class="sxs-lookup"><span data-stu-id="db243-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db243-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db243-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="db243-141">Barındırma</span><span class="sxs-lookup"><span data-stu-id="db243-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
