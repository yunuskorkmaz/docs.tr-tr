---
title: Hizmet Çerçevesi Verileri
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 5c65e9d473b5fe3f2b1c29824dcc1151abb0c3f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780815"
---
# <a name="service-framework-data"></a>Hizmet Çerçevesi Verileri
Bu konu hizmet çerçevesi verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|Belirtilen öğe belirtilen ad geçerli değil. Bu, belirtilen öğeyi bir yinelenen öğe olduğunu ya da uzantı öğeleri adresleme ad alanlarında olamayacağından yasal bir uzantı etkinleştirilmediğini anlamına gelir.|  
|BinaryEncoderSessionInvalid|Önceki bir iletinin şifrelemesini kaldırmada hata yüzünden ikili kodlama oturumu geçerli değil.|  
|CannotDetectAddressingVersion|WS-Addressing sürümü algılanamıyor. EndpointAddress bir öğe ile başlamıyor.|  
|CouldNotFindNamespaceForPrefix|Belirtilen önek ad alanı bağlayıcısı yok kapsamda sahiptir.|  
|EncoderBadContentType|İçin ContentType özniteliği işlenemiyor.|  
|EncoderEnvelopeVersionMismatch|Belirtilen gelen iletinin Zarf sürümü belirtilen Kodlayıcı eşleşmiyor. Bağlamanın beklenen iletilerle aynı sürümle yapılandırıldığından emin olun.|  
|EncoderMessageVersionMismatch|Belirtilen giden iletinin ileti sürümü, belirtilen Kodlayıcı eşleşmiyor. Bağlama yapılacak gibi aynı sürümle yapılandırıldığından emin olun.|  
|ExtraContentIsPresentInFaultDetail|Hata ayrıntı öğesinde ek Genişletilebilir Biçimlendirme Dili içerik yok. Yalnızca bir öğeye izin verilir.|  
|FilterBadTableType|Bir filtre için oluşturulan IMessageFilterTable veya MessageFilterTable türetilmiş bir MessageFilterTable olamaz.|  
|FilterTableInvalidForLookup|MessageFilterTable durumu bozuk. İstenen arama gerçekleştirilemiyor.|  
|MandatoryHeaderNotUnderstood|Bir veya daha fazla Basit Nesne Erişim Protokolü üst bilgisi blokları anlaşılmadı gereklidir.|  
|MessageBodyIsStream|İleti gövdesi bir akıştır.|  
|MessageBodyIsUnknown|İleti gövdesinin biçimi bilinmiyor.|  
|MessageBodyReaderInvalidReadState|İleti gövde Okuyucu, belirtilen ReadState tüketilemiyor.|  
|MessageTextEncodingNotSupported|Metin iletisi biçiminde kullanılan belirtilen metin kodlaması desteklenmiyor.|  
|MissingMessageID|Message, MessageID üst bilgisi eksik isteyin. Bir MessageID üst bilgisi bir Yanıtla ilişkilendirmek için gereklidir.|  
|MultipleMessageHeaders|Ad alanı ve belirtilen ada sahip birden fazla üst bilgi bulundu.|  
|MultipleMessageHeadersWithActor|Belirtilen ad, ad alanı ve rol ile birden fazla üst bilgi bulundu.|  
|MultipleRelatesToHeaders|Belirtilen ilişkide birden fazla RelatesTo üst bilgisi bulunamadı. Her ilişki için yalnızca birine izin verilir.|  
|QueryFunctionTypeNotSupported|Belirtilen tür IXsltContextFunction için desteklenmeyen döndürür.|  
|QueryIteratorOutOfScope|XPathNodeIterator geçersiz hale getirildi. XPathNodeIterator IXsltContextFunction için bağımsız değişken olarak geçirilen değerleri yalnızca işlev içinde geçerlidir. Bunlar daha sonra kullanmak üzere önbelleğe alınmış veya olamaz işlev tarafından döndürülen.|  
|QueryVariableNull|IXsltContextVariable yöntemleri null döndürülemez.|  
|QueryVariableTypeNotSupported|Belirtilen IXsltContextVariable türetilmiş türü desteklenmiyor.|  
|ReceiveShutdownReturnedMessage|Kanal kapatılırken belirtilen eylemle beklenmeyen bir giriş iletisi aldı. Giriş iletisi beklemediğinizde kanal kapatın.|  
|XmlBufferInInvalidState|Bir iç hata oluştu. XML arabelleği durumu nedeniyle işlem gerçekleştirilemiyor.|  
|XmlBufferQuotaExceeded|Genişletilebilir Biçimlendirme Dili içeriğini ara belleğe almak için gereken boyut, ara bellek kotasını aştı.|
