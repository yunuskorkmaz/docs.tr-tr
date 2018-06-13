---
title: Hizmet Çerçevesi Verileri
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 5c65e9d473b5fe3f2b1c29824dcc1151abb0c3f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474022"
---
# <a name="service-framework-data"></a>Hizmet Çerçevesi Verileri
Bu konu hizmet çerçevesi verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|Belirtilen öğe belirtilen ad geçerli değil. Belirtilen öğe yinelenen bir öğe olduğunu veya genişletme öğeleri adresleme ad alanında olamayacağı için yasal bir uzantısı olmadığını anlamına gelir.|  
|BinaryEncoderSessionInvalid|Önceki ileti kod çözme bir hata oluştuğundan ikili kodlama oturum geçerli değil.|  
|CannotDetectAddressingVersion|WS-adresleme sürümü algılanamıyor. EndpointAddress bir öğesiyle başlatılmaz.|  
|CouldNotFindNamespaceForPrefix|Belirtilen önek kapsamındaki hiçbir ad alanı bağlama var.|  
|EncoderBadContentType|İçin contentType işleyemiyor.|  
|EncoderEnvelopeVersionMismatch|Belirtilen gelen ileti Zarf sürümünü belirtilen Kodlayıcı eşleşmiyor. Bağlama beklenen iletiler gibi aynı sürümle yapılandırıldığından emin olun.|  
|EncoderMessageVersionMismatch|Belirtilen giden iletinin ileti sürümü belirtilen Kodlayıcı eşleşmiyor. Bağlama yapılacak aynı sürüme sahip yapılandırıldığından emin olun.|  
|ExtraContentIsPresentInFaultDetail|Ek genişletilebilir biçimleme dili içerik hata ayrıntı öğesinde mevcuttur. Yalnızca tek bir öğe izin verilir.|  
|FilterBadTableType|Bir filtre için oluşturulan IMessageFilterTable veya MessageFilterTable türetilmiş bir MessageFilterTable olamaz.|  
|FilterTableInvalidForLookup|MessageFilterTable durumu bozuk. İstenen araması gerçekleştirilemez.|  
|MandatoryHeaderNotUnderstood|Bir veya daha fazla Basit Nesne Erişim Protokolü üstbilgi blokları değil anladım gerekli.|  
|MessageBodyIsStream|İleti gövdesi bir akışı'dır.|  
|MessageBodyIsUnknown|İleti gövdesinin biçimi bilinmiyor.|  
|MessageBodyReaderInvalidReadState|İleti gövdesi Okuyucu, belirtilen ReadState kullanılamaz.|  
|MessageTextEncodingNotSupported|Belirtilen metni metin iletisi biçiminde kullanılan kodlama desteklenmiyor.|  
|MissingMessageID|İleti bir MessageID üstbilgisi eksik isteyin. Bir MessageID üstbilgisi bir Yanıtla ilişkilendirmek için gereklidir.|  
|MultipleMessageHeaders|Belirtilen ada ve ad alanı ile birden fazla üst bilgi bulunamadı.|  
|MultipleMessageHeadersWithActor|Belirtilen ad, ad alanı ve rol ile birden fazla üst bilgi bulunamadı.|  
|MultipleRelatesToHeaders|Belirtilen ilişki sahip birden fazla RelatesTo üstbilgi bulundu. Her ilişki için yalnızca birine izin verilir.|  
|QueryFunctionTypeNotSupported|Belirtilen IXsltContextFunction türünün desteklenmediğini döndür.|  
|QueryIteratorOutOfScope|XPathNodeIterator doğrulanmadı. IXsltContextFunction için bağımsız değişken olarak geçirilen XPathNodeIterator değerleri yalnızca işlev içinde geçerlidir. Bunlar daha sonra kullanmak için önbelleğe alınmış veya değiştirilemez işlev tarafından döndürülen.|  
|QueryVariableNull|IXsltContextVariable yöntemleri null döndüremez.|  
|QueryVariableTypeNotSupported|Belirtilen IXsltContextVariable türetilmiş türü desteklenmiyor.|  
|ReceiveShutdownReturnedMessage|Kanal kapatılırken belirtilen eylemi olan beklenmeyen bir giriş iletisi aldı. Daha fazla giriş iletileriniz beklemeyen zaman kanal kapatın.|  
|XmlBufferInInvalidState|Bir iç hata oluştu. XML arabelleği durumu nedeniyle işlem gerçekleştirilemiyor.|  
|XmlBufferQuotaExceeded|Genişletilebilir Biçimleme Dili içeriği arabellek gerekli boyutu ara bellek kotasını aştı.|
