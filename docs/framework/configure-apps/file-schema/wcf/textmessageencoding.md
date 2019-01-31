---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: c9f8347b4ee5f8fdbcf5c65c9a38b171ea6309de
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289607"
---
# <a name="textmessageencoding"></a>\<textMessageEncoding >
Karakter kodlamasını ve ileti sürüm oluşturmayı metin tabanlı XML iletileri için kullanılan belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<textMessageEncoding >  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|maxReadPoolSize|İleti sayısını belirten bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz. Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek. 64 varsayılandır.|  
|maxWritePoolSize|İleti sayısını belirten bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek. Daha büyük havuz boyutları sistemi daha büyük bir çalışma kümesi, etkinlik artışlarını daha dayanıklı hale getirmek. Varsayılan değer 16'dır.|  
|messageVersion|Bağlama kullanılarak gönderilen iletilerin SOAP sürümünü belirtir. Geçerli değerler:<br /><br /> -Soap11Addressing10<br />-Soap12Addressing10<br /><br /> Soap12Addressing10 varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Bağlamadaki yayma iletileri için kullanılacak kodlama karakter kümesini belirtir. Geçerli değerler:<br /><br /> -   UnicodeFffeTextEncoding: Unicode kodlama BigEndian<br />-   Utf16TextEncoding: Unicode kodlama<br />-   Utf8TextEncoding: 8-bit kodlama<br /><br /> Utf8TextEncoding varsayılandır. Bu öznitelik türünde <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kodlama bir ileti bir dizi bayta dönüştürme işlemidir. Kod çözme ters işlemidir. Windows Communication Foundation (WCF) için SOAP iletilerini kodlama üç türlerini içerir: Metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM).  
  
 Metin kodlaması ile temsil edilen `textMessageEncoding` öğedir en birlikte çalışabilir, ancak XML iletileri için en az verimli Kodlayıcı.  Metin Kodlayıcı kablo metin tabanlı iletileri oluşturur. Bu Kodlayıcı tarafından üretilen iletileri, WS - için uygun * Interop bağlı. Web hizmeti veya Web hizmeti istemcisi, metinsel XML genellikle anlayabilirsiniz. Ancak, büyük metin olarak ikili veri blokları iletme XML iletileri kodlama az verimli yöntemdir.  
  
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
- [İleti Kodlayıcı Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [İleti Kodlama](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
