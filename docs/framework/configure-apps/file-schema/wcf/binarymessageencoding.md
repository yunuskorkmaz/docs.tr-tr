---
title: '&lt;binaryMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 503c0edf3a21b3fb0f57b5199aa2a1a17df4222d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbinarymessageencodinggt"></a>&lt;binaryMessageEncoding&gt;
Windows Communication Foundation (WCF) iletilerinde hattaki ikili kodlar bir ikili ileti Kodlayıcısı tanımlar.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<binaryMessageEncoding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"   messageVersion="Soap11Addressing10/Soap12Addressing10" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|maxReadPoolSize|Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz. Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun. 64 varsayılandır.|  
|maxSessionSize|Kodlama için kullanılan arabelleğin bayt cinsinden boyutu ayarlar pozitif bir tamsayı. Daha büyük bir arabellek çalışma kümesi boyutu ödün verme pahasına kodlama hızını artırır. Varsayılan 2048'dir.|  
|maxWritePoolSize|Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir. Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun. 16 varsayılandır.|  
|messageVersion|SOAP iletisi ve beklenmeyen veya kullanılan WS adresleme sürümleri belirtir.|  
  
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
  
 `binaryMessageEncoding` Öğesi için XML .NET ikili biçimini belirtir ve karakter kodlamasını belirtmek için seçenekler ve kullanılacak SOAP ve WS adresleme sürümü vardır. İkili ileti Kodlayıcı ikili hat üzerinde Windows Communication Foundation (WCF) iletilerinde kodlar. Bu kodlama ileti çok hızlı aktarımını sonuçları, birlikte çalışabilirlik tabanlı WS - üzerinde * standartları kaybolur.  
  
## <a name="example"></a>Örnek  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [İleti Kodlama](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [İleti Kodlayıcı Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
