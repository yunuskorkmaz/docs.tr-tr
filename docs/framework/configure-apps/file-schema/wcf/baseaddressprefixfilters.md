---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 378db238d647be2248c0303f45aece42f7ea5b31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701014"
---
# <a name="baseaddressprefixfilters"></a>\<baseAddressPrefixFilters>
IIS'de Windows Communication Foundation (WCF) uygulama uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlar filtreleri belirten geçişine yapılandırma koleksiyonunu temsil eder.  
  
> [!WARNING]
>  \<baseAddressPrefixFilters > değil "localhost" olarak tanıyacak, bunun yerine tam makine adını kullanın.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|Önek filtresi için hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğesi ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Belirli bir hizmet barındırma ortamını gösteren türü tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Önek filtresi, hangi bir URI'leri olan hizmet tarafından kullanılmak üzere belirtmek paylaşılan barındırma sağlayıcıları için bir yol sağlar. Bu, birden çok uygulama ile aynı sitede aynı düzeni için farklı temel adresler barındırmak için paylaşılan ana bilgisayarları etkinleştirir.  
  
 IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcılardır. Uygulama bir sitedeki bir veya daha fazla IIS bağlamaları erişilebilir. IIS bağlamaları, iki bilgi parçasını sağlar: bağlama protokolü ve bağlama bilgileri. İletişim oluştuğu Düzen Protokolü (örneğin, HTTP) bağlama tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, AnaBilgisayarÜstbilgisi) siteye erişmek için kullanılan verileri içerir.  
  
 IIS, her şeması için birden çok taban adresi sonuçlanır her site için birden fazla IIS bağlamaları belirtme destekler. Bir site altında barındırılan bir WCF hizmeti yalnızca bir temel adres bir bağlamayı her şeması için izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtreleme özelliğini kullanabilirsiniz. IIS tarafından sağlanan gelen temel adresler, isteğe bağlı bir ön ek listesi filtre göre filtrelenir.  
  
 Örneğin, siteniz aşağıdaki temel adresler içerebilir.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Uygulama etki alanı düzeyinde bir önek filtre belirtmek için aşağıdaki yapılandırma dosyası kullanabilirsiniz.  
  
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
  
 Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` aracılığıyla geçirilmesine izin verilir, kendi şemaları için yalnızca temel adresleridir.  
  
 Öneki belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir. Önek belirleyerek eşleşen temel adresini doğrudan geçiş yapılacak bu şema için yalnızca sağlar.  
  
> [!NOTE]
>  Filtre, herhangi bir joker karakterleri desteklemiyor. Ayrıca, IIS tarafından sağlanan baseAddresses adresleri yok diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi. Bu adresleri filtrelenir değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
