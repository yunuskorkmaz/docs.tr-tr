---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8c15b06e60e4de6ede4c9a683a6701140533534c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204742"
---
# \<mexHttpBinding>

HTTP üzerinde WS-MetadataExchange (WS-MEX) ileti değişimi için kullanılan bir bağlamanın ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|`name`|Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|`openTimeout`|Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|`receiveTimeout`|<xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:10:00 ' dir.|  
|`sendTimeout`|<xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu bağlama temelde `WSHttpBinding` güvenlik devre dışı olan bir bağlamadır. Meta veri isteklerinin çoğunu destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [Meta veriler](../../../wcf/feature-details/metadata.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
