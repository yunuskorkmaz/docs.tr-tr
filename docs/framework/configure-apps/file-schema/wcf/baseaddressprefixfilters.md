---
description: 'Hakkında daha fazla bilgi edinin: <baseAddressPrefixFilters>'
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 9212838393ead04bdcd475b314bb2707e6f899ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749681"
---
# \<baseAddressPrefixFilters>

IIS 'de Windows Communication Foundation (WCF) uygulamasını barındırırken uygun Internet Information Services (IIS) bağlamalarını seçmek için bir mekanizma sağlayan geçiş filtrelerini belirten yapılandırma öğelerinin bir koleksiyonunu temsil eder.  
  
> [!WARNING]
> \<baseAddressPrefixFilters> "localhost" öğesini tanımıyor; Bunun yerine tam makine adını kullanın.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**  
  
## <a name="syntax"></a>Syntax  
  
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
|[\<add>](add-of-baseaddressprefixfilter.md)|Hizmet ana bilgisayarı tarafından kullanılan taban adresler için önek filtresini belirten bir yapılandırma öğesi ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Önek filtresi, paylaşılan barındırma sağlayıcılarının, hizmet tarafından hangi URI 'Lerin kullanılacağını belirtmek için bir yol sağlar. Paylaşılan ana bilgisayarların aynı sitede aynı düzen için farklı temel adreslere sahip birden çok uygulamayı barındırmalarını sağlar.  
  
 IIS Web siteleri, sanal dizinler içeren sanal uygulamalara yönelik kapsayıcılardır. Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir. IIS bağlamaları iki adet bilgi sağlar: bağlama protokolü ve bağlama bilgileri. Bağlama Protokolü (örneğin, HTTP), iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri (örneğin, IP adresi, bağlantı noktası, hostheader) siteye erişmek için kullanılan verileri içerir.  
  
 IIS, her bir site için birden çok IIS bağlaması belirtmeyi destekler ve bu, her bir şema için birden çok temel adrese neden Bir site altında barındırılan bir WCF hizmeti her bir şema için yalnızca bir temel adrese bağlamaya izin verdiğinden, barındırılan hizmetin gerekli temel adresini seçmek için önek filtresi özelliğini kullanabilirsiniz. IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek listesi filtresine göre filtrelenir.  
  
 Örneğin, siteniz aşağıdaki temel adresleri içerebilir:
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Uygulama etki alanı düzeyinde bir önek filtresi belirtmek için aşağıdaki yapılandırma dosyasını kullanabilirsiniz.  
  
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
  
 Bu örnekte, `net.tcp://test1.fabrikam.com:8000` ve `http://test2.fabrikam.com:9000` kendisine geçirilmesine izin verilen kendi şemaları için tek temel adreslerdir.  
  
 Varsayılan olarak, ön ek belirtilmediğinde tüm adresler geçirilir. Ön eki belirtmek yalnızca ilgili düzenin eşleşen temel adresinin geçirilmesine izin verir.  
  
> [!NOTE]
> Filtre herhangi bir joker karakteri desteklemiyor. Buna ek olarak, IIS tarafından sağlanan baseAddresses, listede bulunmayan diğer şemalara göre adreslere sahip olabilir `baseAddressPrefixFilters` . Bu adresler filtrelenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hosting](../../../wcf/feature-details/hosting.md)
