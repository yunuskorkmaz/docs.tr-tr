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
# <a name="baseaddressprefixfilters"></a>\<baseAddressPrefixFiltreler>
IIS'de Windows Communication Foundation (WCF) uygulamasını barındırırken uygun Internet Bilgi Hizmetleri (IIS) bağlaçlarını seçmek için bir mekanizma sağlayan filtrelerden geçiş belirten yapılandırma öğeleri koleksiyonunu temsil eder.  
  
> [!WARNING]
> \<baseAddressPrefixFilters> "localhost"u tanımıyor; bunun yerine tam nitelikli makine adını kullanın.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingÇevre>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFiltreler>**  
  
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
|[\<>ekleyin](add-of-baseaddressprefixfilter.md)|Hizmet ana bilgisayarı tarafından kullanılan temel adresler için önek filtresi belirten bir yapılandırma öğesi ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceHostingÇevre>](servicehostingenvironment.md)|Hizmet barındırma ortamının belirli bir aktarım için anlık olarak çalıştığı türü tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Önek filtresi, paylaşılan barındırma sağlayıcılarının hizmet tarafından hangi URL'lerin kullanılacağını belirtmelerine yol sağlar. Paylaşılan ana bilgisayarların aynı sitede aynı şemaya yönelik farklı temel adreslere sahip birden çok uygulamayı barındırmasını sağlar.  
  
 IIS Web siteleri, sanal dizinler içeren sanal uygulamalar için kapsayıcılardır. Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir. IIS ciltlemeleri iki bilgi parçası sağlar: bağlama protokolü ve bağlayıcı bilgiler. Bağlama protokolü (örneğin, HTTP) iletişimin gerçekleştiği düzeni tanımlar ve bağlayıcı bilgiler (örneğin, IP Adresi, Bağlantı Noktası, Ana Bilgisayar) siteye erişmek için kullanılan verileri içerir.  
  
 IIS, her site için birden çok IIS bağlayıcısı belirtmeyi destekler ve bu da her düzen için birden çok temel adresle sonuçlanır. Bir site altında barındırılan bir WCF hizmeti, her düzen için yalnızca bir temel adrese bağlamaya izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtresi özelliğini kullanabilirsiniz. IIS tarafından sağlanan gelen temel adresler isteğe bağlı öneek listesi filtresine göre filtrelenir.  
  
 Örneğin, siteniz aşağıdaki temel adresleri içerebilir:
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Appdomain düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyasını kullanabilirsiniz.  
  
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
  
 Bu örnekte `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` ve kendi şemaları için geçirilen izin verilen tek temel adresleri vardır.  
  
 Varsayılan olarak, önek belirtilmediğinde, tüm adresler geçirilir. Önek belirtilmesi yalnızca bu düzenin eşleşen temel adresinin geçirilmesine izin verir.  
  
> [!NOTE]
> Filtre herhangi bir joker karakter desteklemez. Ayrıca, IIS tarafından sağlanan temel Adresler `baseAddressPrefixFilters` listede bulunmayan diğer düzenlere bağlı adreslere sahip olabilir. Bu adresler filtreuygulanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Barındırma](../../../wcf/feature-details/hosting.md)
