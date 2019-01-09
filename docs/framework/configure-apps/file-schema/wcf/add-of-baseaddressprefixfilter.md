---
title: '&lt;baseAddressPrefixFilter&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: ece3178c48c84c609ab959a5cfc426062de9255f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145607"
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a><span data-ttu-id="105ea-102">&lt;baseAddressPrefixFilter&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="105ea-102">&lt;add&gt; of &lt;baseAddressPrefixFilter&gt;</span></span>
<span data-ttu-id="105ea-103">IIS içinde bir Windows Communication Foundation (WCF) uygulaması uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlayan doğrudan bir filtre belirtir bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="105ea-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="105ea-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="105ea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="105ea-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="105ea-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="105ea-106">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="105ea-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="105ea-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="105ea-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105ea-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="105ea-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="105ea-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="105ea-109">Attributes and Elements</span></span>  
 <span data-ttu-id="105ea-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="105ea-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="105ea-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="105ea-111">Attributes</span></span>  
  
|<span data-ttu-id="105ea-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="105ea-112">Attribute</span></span>|<span data-ttu-id="105ea-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="105ea-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="105ea-114">Ön eki</span><span class="sxs-lookup"><span data-stu-id="105ea-114">prefix</span></span>|<span data-ttu-id="105ea-115">Temel adres bir kısmen eşleştirmek için kullanılan URI.</span><span class="sxs-lookup"><span data-stu-id="105ea-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="105ea-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="105ea-116">Child Elements</span></span>  
 <span data-ttu-id="105ea-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="105ea-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="105ea-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="105ea-118">Parent Elements</span></span>  
  
|<span data-ttu-id="105ea-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="105ea-119">Element</span></span>|<span data-ttu-id="105ea-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="105ea-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="105ea-121">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="105ea-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="105ea-122">IIS içinde bir Windows Communication Foundation (WCF) uygulaması uygun IIS bağlamalarını seçmek için bir mekanizma sağlar doğrudan filtreleri belirten yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="105ea-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="105ea-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="105ea-123">Remarks</span></span>  
 <span data-ttu-id="105ea-124">Önek filtresi, hangi bir URI'leri olan hizmet tarafından kullanılmak üzere belirtmek paylaşılan barındırma sağlayıcıları için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="105ea-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="105ea-125">Bu, birden çok uygulama ile aynı sitede aynı düzeni için farklı temel adresler barındırmak için paylaşılan ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="105ea-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="105ea-126">IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="105ea-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="105ea-127">Uygulama bir sitedeki bir veya daha fazla IIS bağlama aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="105ea-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="105ea-128">IIS bağlamaları, iki bilgi parçasını sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="105ea-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="105ea-129">İletişim oluştuğu Düzen Protokolü (örneğin, HTTP) bağlama tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, AnaBilgisayarÜstbilgisi) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="105ea-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="105ea-130">IIS, her şeması için birden çok taban adresi sonuçlanır her site için birden fazla IIS bağlamaları belirtme destekler.</span><span class="sxs-lookup"><span data-stu-id="105ea-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="105ea-131">Bir site altında barındırılan bir WCF hizmeti yalnızca bir temel adres bir bağlamayı her şeması için izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtreleme özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="105ea-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="105ea-132">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı bir ön ek listesi filtre göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="105ea-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="105ea-133">Örneğin, siteniz aşağıdaki temel adresler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="105ea-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="105ea-134">Uygulama etki alanı düzeyinde bir önek filtre belirtmek için aşağıdaki yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="105ea-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="105ea-135">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` doğrudan geçiş yapılacak izin, kendi şemaları için yalnızca temel adresleridir.</span><span class="sxs-lookup"><span data-stu-id="105ea-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="105ea-136">Öneki belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="105ea-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="105ea-137">Önek belirleyerek eşleşen temel adresini doğrudan geçiş yapılacak bu şema için yalnızca sağlar.</span><span class="sxs-lookup"><span data-stu-id="105ea-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="105ea-138">Filtre, herhangi bir joker karakterleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="105ea-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="105ea-139">Ayrıca, IIS tarafından sağlanan baseAddresses adresleri yok diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi.</span><span class="sxs-lookup"><span data-stu-id="105ea-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="105ea-140">Bu adresleri filtrelenir değil.</span><span class="sxs-lookup"><span data-stu-id="105ea-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105ea-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="105ea-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="105ea-142">Barındırma</span><span class="sxs-lookup"><span data-stu-id="105ea-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
