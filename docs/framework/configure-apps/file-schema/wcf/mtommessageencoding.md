---
title: '&lt;mtomMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc7db79f25e2ab202f79f7f4ab5cc2a0e5eb0242
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmtommessageencodinggt"></a>&lt;mtomMessageEncoding&gt;
SOAP iletisi iletim en iyi duruma getirme mekanizmasını (temel MTOM) iletiler için kullanılan kodlama ve ileti sürüm belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<mtomMessageEncoding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
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
|maxBufferSize|Kullanılabilir arabelleğinin maksimum boyutunu belirten bir tamsayı.|  
|maxReadPoolSize|Kaç tane iletileri belirten bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz. Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun. 64 varsayılandır.|  
|maxWritePoolSize|Kaç tane iletileri belirten bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir. Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun. 16 varsayılandır.|  
|messageVersion|Bağlama kullanılarak gönderilen iletileri SOAP sürümünü belirtir. Geçerli değerler:<br /><br /> -Soap11Addressing1<br />-Soap12Addressing10<br /><br /> Soap12Addressing10 varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Karakter bağlama verme iletileri için kullanılacak kodlama kümesini belirtir. Geçerli değerler:<br /><br /> -UnicodeFffeTextEncoding: Unicode kodlama BigEndian<br />-Utf16TextEncoding: Unicode kodlama<br />-Utf8TextEncoding: 8 bit kodlama<br /><br /> Utf8TextEncoding varsayılandır. Bu öznitelik türünde <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kodlama bayt dizisi bir ileti dönüştürme işlemidir. Kod çözme ters bir işlemdir. Windows Communication Foundation (WCF) SOAP iletiler için kodlamayı üç türleri içerir: metin ve ikili ileti iletim en iyi duruma getirme mekanizmasını (MTOM).  
  
 `MtomMessageEncoding` Öğesi karakter kodlama ve ileti sürüm oluşturma ve bir ileti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlama kullanılarak iletiler için kullanılan diğer ayarları belirtir. MTOM WCF iletilerindeki ikili veri iletmek için verimli bir teknolojidir. MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır. MTOM kodlama çoğu XML metin biçiminde aktarır ancak bunları olarak ileterek büyük ikili veri blokları en iyi duruma getirir-base64 ile kodlanmış biçimlerini dönüştürme olmadan, ise.  
  
## <a name="example"></a>Örnek  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [İleti Kodlama](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [İleti Kodlayıcı Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
