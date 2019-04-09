---
title: <add> , <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: a58a29e44fff3d653d04da271e3b240f2969611f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143903"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="339e0-102">\<Ekle >, \<baseAddressPrefixFilter ></span><span class="sxs-lookup"><span data-stu-id="339e0-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="339e0-103">IIS içinde bir Windows Communication Foundation (WCF) uygulaması uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlayan doğrudan bir filtre belirtir bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="339e0-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="339e0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="339e0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="339e0-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="339e0-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="339e0-106">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="339e0-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="339e0-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="339e0-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="339e0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="339e0-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="339e0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="339e0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="339e0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="339e0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="339e0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="339e0-111">Attributes</span></span>  
  
|<span data-ttu-id="339e0-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="339e0-112">Attribute</span></span>|<span data-ttu-id="339e0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="339e0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="339e0-114">Ön eki</span><span class="sxs-lookup"><span data-stu-id="339e0-114">prefix</span></span>|<span data-ttu-id="339e0-115">Temel adres bir kısmen eşleştirmek için kullanılan URI.</span><span class="sxs-lookup"><span data-stu-id="339e0-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="339e0-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="339e0-116">Child Elements</span></span>  
 <span data-ttu-id="339e0-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="339e0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="339e0-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="339e0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="339e0-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="339e0-119">Element</span></span>|<span data-ttu-id="339e0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="339e0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="339e0-121">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="339e0-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="339e0-122">IIS içinde bir Windows Communication Foundation (WCF) uygulaması uygun IIS bağlamalarını seçmek için bir mekanizma sağlar doğrudan filtreleri belirten yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="339e0-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="339e0-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="339e0-123">Remarks</span></span>  
 <span data-ttu-id="339e0-124">Önek filtresi, hangi bir URI'leri olan hizmet tarafından kullanılmak üzere belirtmek paylaşılan barındırma sağlayıcıları için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="339e0-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="339e0-125">Bu, birden çok uygulama ile aynı sitede aynı düzeni için farklı temel adresler barındırmak için paylaşılan ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="339e0-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="339e0-126">IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="339e0-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="339e0-127">Uygulama bir sitedeki bir veya daha fazla IIS bağlama aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="339e0-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="339e0-128">IIS bağlamaları, iki bilgi parçasını sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="339e0-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="339e0-129">İletişim oluştuğu Düzen Protokolü (örneğin, HTTP) bağlama tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, AnaBilgisayarÜstbilgisi) siteye erişmek için kullanılan verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="339e0-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="339e0-130">IIS, her şeması için birden çok taban adresi sonuçlanır her site için birden fazla IIS bağlamaları belirtme destekler.</span><span class="sxs-lookup"><span data-stu-id="339e0-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="339e0-131">Bir site altında barındırılan bir WCF hizmeti yalnızca bir temel adres bir bağlamayı her şeması için izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtreleme özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="339e0-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="339e0-132">IIS tarafından sağlanan gelen temel adresler, isteğe bağlı bir ön ek listesi filtre göre filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="339e0-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="339e0-133">Örneğin, siteniz aşağıdaki temel adresler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="339e0-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="339e0-134">Uygulama etki alanı düzeyinde bir önek filtre belirtmek için aşağıdaki yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="339e0-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="339e0-135">Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` doğrudan geçiş yapılacak izin, kendi şemaları için yalnızca temel adresleridir.</span><span class="sxs-lookup"><span data-stu-id="339e0-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="339e0-136">Öneki belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="339e0-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="339e0-137">Önek belirleyerek eşleşen temel adresini doğrudan geçiş yapılacak bu şema için yalnızca sağlar.</span><span class="sxs-lookup"><span data-stu-id="339e0-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="339e0-138">Filtre, herhangi bir joker karakterleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="339e0-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="339e0-139">Ayrıca, IIS tarafından sağlanan baseAddresses adresleri yok diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi.</span><span class="sxs-lookup"><span data-stu-id="339e0-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="339e0-140">Bu adresleri filtrelenir değil.</span><span class="sxs-lookup"><span data-stu-id="339e0-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339e0-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="339e0-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="339e0-142">Barındırma</span><span class="sxs-lookup"><span data-stu-id="339e0-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
