---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: c5cd8e9e2002f44fd9feebdc6bb7ede023de459a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556453"
---
# \<textMessageEncoding>
Metin tabanlı XML iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|maxReadPoolSize|Yeni okuyucu ayırmadan aynı anda okunabilecek ileti sayısını belirten bir tamsayı. Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir. Varsayılan değer 64 ' dir.|  
|maxWritePoolSize|Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını belirten bir tamsayı. Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir. Varsayılan değer 16 ' dır.|  
|messageVersion|Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir. Geçerli değerler şunlardır<br /><br /> - Soap11Addressing10<br />- Soap12Addressing10<br />- Soap11<br />- Soap12<br /><br />Varsayılan değer Soap12Addressing10 ' dir. Bu öznitelik türü <xref:System.ServiceModel.Channels.MessageVersion> .|  
|writeEncoding|Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir. Geçerli değerler şunlardır<br /><br /> -Unicodefffebir kodlama: Unicode Bigenyen kodlaması<br />-Utf16TextEncoding: Unicode kodlaması<br />-Utf8TextEncoding: 8 bit kodlama<br /><br /> Varsayılan değer Utf8TextEncoding ' dir. Bu öznitelik türü <xref:System.Text.Encoding> .|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir. Kod çözme işlemi ters işlemdir. Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).  
  
 Öğesi tarafından temsil edilen metin kodlaması `textMessageEncoding` en çok çalışabilen, ancak xml iletileri için en az verimli kodlayıcıdır.  Metin Kodlayıcısı, tel üzerinde metin tabanlı iletiler oluşturur. Bu kodlayıcı tarafından üretilen iletiler WS-* tabanlı birlikte çalışma için uygundur. Web hizmeti veya Web hizmeti istemcisi, genellikle metinsel XML 'i anlayabilir. Ancak, büyük ikili veri bloklarını metin olarak iletme, XML iletilerini kodlamak için en düşük verimli yöntemdir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [İleti Kodlayıcı Seçme](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [İleti Kodlama](message-encoding.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
