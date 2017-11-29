---
title: '&lt;webMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e6257721f8b85296d4da28cc036c946f6357c11b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebmessageencodinggt"></a>&lt;webMessageEncoding&gt;
Düz metin XML, JavaScript nesne gösterimi (JSON) ileti Kodlamalar ve okunabilir ve yazılabilir kullanıldığında "ham" ikili içeriğini sağlayan bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bağlama.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<webMessageEncoding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maxReadPoolSize`|Yeni okuyucu ayırmadan aynı anda okunabilir iletilerin miktarı. Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun. 64 okuyucular her iç kodlayıcılar (yalnızca metin, JSON ve "ham") için varsayılandır.<br /><br /> Bu sayı artar bellek tüketimi artırılması, ancak yeni kampanya oluşturmak yerine zaten oluşturulmuştur havuz okuyuculardan kullanmanız mümkün olduğundan gelen iletileri ani WINS'e ile mücadele etmek için Kodlayıcı hazırlar.|  
|`maxWritePoolSize`|Yeni yazıcı ayırmadan aynı anda gönderilebilir iletilerin miktarı. Daha büyük havuzu boyutları sistem büyük bir çalışma kümesi, etkinlik ani daha dayanıklı olun. Her iç kodlayıcılar (yalnızca metin, JSON ve "ham") için 16 yazıcılarının varsayılandır.<br /><br /> Bu sayı artar bellek tüketimi artırılması, ancak yeni kampanya oluşturmak yerine, önceden oluşturulan yazıcılarının havuzundan kullanmanız mümkün olduğundan Giden iletiler ani WINS'e ile mücadele etmek için Kodlayıcı hazırlar.|  
|`writeEncoding`|Karakter bağlama verme iletileri için kullanılacak kodlama kümesini belirtir. Geçerli değerler şunlardır:<br /><br /> -UnicodeFffeTextEncoding: Unicode Big Endian'ya kodlaması.<br />-Utf16TextEncoding: Unicode kodlama.<br />-Utf8TextEncoding: 8 bit kodlama.<br /><br /> Utf8TextEncoding varsayılandır. Bu öznitelik türünde <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kodlama bayt dizisi bir ileti dönüştürme işlemidir. Kod çözme ters bir işlemdir. Bu işlemler karakter kodlamasını belirtim gerektirir.  
  
 `webMessageEncoding` Öğesi çalışır düz metin XML ve JSON Kodlamalar ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcılar için temsilci. Bu temsilci bileşik ileti Kodlayıcı tarafından gerçekleştirilir.  
  
 Bu bağlama öğesi ve kendi bileşik Kodlayıcı tarafından kullanılan SOAP Mesajlaşma kullanmayın senaryolarda kodlama denetlemek için kullanılan `webHttpBinding` öğesi. Bu senaryolar, "Düz eski XML" (POX), temsili durum aktarımı (REST), dağıtım, gerçekten basit dağıtım (RSS) ve Atom ve zaman uyumsuz JavaScript ve XML (AJAX) içerir. Bileşik ileti Kodlayıcı SOAP veya WS adresleme desteklemez.  
  
 Bağlama öğesi bir yazma karakter kullanarak kodlama ile yapılandırılabilir `writeEncoding` özniteliği. Sağlanan <xref:System.Text.Encoding> değeri JSON ve metin XML örnekleri için yazma davranışını belirtir. Üzerinde okuma, tüm geçerli ileti kodlama ve metin kodlaması anladım.  
  
 `maxReadPoolSize`ve `maxWritePoolSize` okuyucuları ve yazıcıları sırasıyla ayrılacak en fazla sayısını ayarlamak için de kullanılabilir. Varsayılan olarak, 64 okuyucuları ve 16 yazıcıları ayrılır.  
  
 Varsayılan karmaşıklık kısıtlamaları da ayarlanır kullanarak [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) öğesi (DOS) hizmet reddi sınıfının karşı korumak için uç nokta işlemeyi bağlamanın ileti karmaşıklık kullanmak için bu girişim saldırıları kaynaklar.  
  
## <a name="example"></a>Örnek  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [İleti kodlama](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [İleti Kodlayıcı seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
