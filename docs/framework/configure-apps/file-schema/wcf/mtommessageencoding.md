---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 70a124fda5bc0e52e1271716f7e2166b7717b49a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933199"
---
# <a name="mtommessageencoding"></a>\<mtomMessageEncoding >
SOAP Ileti Iletimi Iyileştirme mekanizması (MTOM) tabanlı iletiler için kullanılan kodlama ve ileti sürüm oluşturmayı belirtir.  
  
 \<system.serviceModel>  
\<bağlama >  
\<customBinding >  
\<bağlama >  
\<mtomMessageEncoding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|maxBufferSize|Kullanılabilen arabelleğin en büyük boyutunu belirten bir tamsayı.|  
|maxReadPoolSize|Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı. Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir. Varsayılan değer 64 ' dir.|  
|maxWritePoolSize|Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı. Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir. Varsayılan değer 16 ' dır.|  
|messageVersion|Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir. Geçerli değerler şunlardır<br /><br /> - Soap11Addressing1<br />- Soap12Addressing10<br /><br /> Varsayılan değer Soap12Addressing10 ' dir. Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir. Geçerli değerler şunlardır<br /><br /> -Unicodefffebir kodlama: Unicode Bigenyen kodlaması<br />- Utf16TextEncoding: Unicode kodlaması<br />- Utf8TextEncoding: 8 bit kodlama<br /><br /> Varsayılan değer Utf8TextEncoding ' dir. Bu öznitelik türü <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../misc/binding.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir. Kod çözme işlemi ters işlemdir. Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: Metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).  
  
 `MtomMessageEncoding` Öğesi, bir ileti iletimi iyileştirme mekanizması (MTOM) kodlaması kullanan iletiler için kullanılan karakter kodlamasını ve ileti sürümü oluşturmayı ve diğer ayarları belirtir. MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir. MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır. MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bunları olduğu gibi ileterek, Base64 kodlamalı biçime dönüştürülmeksizin büyük ikili veri bloklarını iyileştirir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [İleti Kodlama](message-encoding.md)
- [İleti Kodlayıcı Seçme](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
