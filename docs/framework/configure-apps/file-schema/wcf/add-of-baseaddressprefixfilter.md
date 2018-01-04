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
ms.workload: dotnet
ms.openlocfilehash: ad6ad6f71ef015ad97a2688a7334e8a0c6e5af44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a>&lt;baseAddressPrefixFilter&gt; &lt;ekleme&gt;
Uygun Internet Information Services (IIS) bağları barındırırken seçmek için bir mekanizma sağlar bir geçiş filtre belirten bir yapılandırma öğesi temsil eden bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] IIS'de uygulama.  
  
 \<Sistem. ServiceModel >  
\<ServiceHostingEnvironment >  
\<baseAddressPrefixFilters >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|önek|Temel adres kısmen eşleştirmek için kullanılan bir URI.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Uygun IIS bağları barındırırken seçmek için bir mekanizma sağlar geçiş filtrelerini belirtme yapılandırma öğeleri koleksiyonu bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] IIS'de uygulama.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir önek filtre, hangi URI'ler olan hizmet tarafından kullanılmak üzere belirtmek paylaşılan barındırma hizmeti sağlayıcıları için bir yol sağlar. Birden çok uygulama aynı sitedeki aynı düzeni için farklı temel adresleriyle barındırmak paylaşılan konakları sağlar.  
  
 IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcı görevi görür. Uygulama bir sitedeki bir veya daha fazla IIS bağlama aracılığıyla erişilebilir. IIS bağlamaları iki parça bilgi sağlar: bağlama protokolü ve bağlama bilgileri. Bağlama Protokolü (örneğin, HTTP) üzerinden iletişimin şeması tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, AnaBilgisayarÜstbilgisi) siteye erişmek için kullanılan verileri içerir.  
  
 IIS, her şeması için birden çok taban adresi sonuçlanan her site için birden çok IIS bağlamaları belirtmeyi destekler. Çünkü bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir site altında barındırılan hizmet sağlayan her şeması için yalnızca bir temel adres için bağlama, barındırılan hizmet gerekli temel adresini seçmek için önek filtre özelliğini kullanabilirsiniz. IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek liste filtresi göre filtrelenir.  
  
 Örneğin, siteniz aşağıdaki temel adresler içerebilir.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Uygulama etki alanı düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyası kullanabilirsiniz.  
  
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
  
 Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` üzerinden iletilecek izin kendi ilgili şemaları için yalnızca temel adresleridir.  
  
 Önek belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir. Önek belirtme yalnızca eşleşen taban adresi üzerinden iletilecek Bu plan için izin verir.  
  
> [!NOTE]
>  Filtre herhangi joker karakterleri desteklemez. Ayrıca, IIS tarafından sağlanan baseAddresses adresleri değil diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi. Bu adresler filtrelendi değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
