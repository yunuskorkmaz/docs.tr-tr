---
title: Hizmet Çerçevesi Verileri
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 8bb6e9df6a77eda5875981a0bf7783f50671a589
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255786"
---
# <a name="service-framework-data"></a>Hizmet Çerçevesi Verileri

Bu konu, Service Framework verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|Addressingextensionınbadns|Belirtilen ad alanındaki belirtilen öğe geçerli değil. Bu, belirtilen öğenin yinelenen bir öğe olduğu veya uzantı öğeleri adresleme ad alanında olamayacağı için geçerli bir uzantı olmadığı anlamına gelir.|  
|Binaryencodersessiongeçersiz|Önceki iletinin kodunu çözerken bir hata oluştuğundan, ikili kodlayıcı oturumu geçerli değil.|  
|CannotDetectAddressingVersion|WS-Addressing sürümü algılanamıyor. EndpointAddress bir öğe ile başlamıyor.|  
|Hayır Dnotfindnamespaceforprefix|Belirtilen önekin kapsamda ad alanı bağlaması yok.|  
|EncoderBadContentType|ContentType öğesine işlenemiyor.|  
|EncoderEnvelopeVersionMismatch|Belirtilen gelen iletinin zarf sürümü belirtilen kodlayıcı ile eşleşmiyor. Bağlamanın beklenen iletilerle aynı sürümle yapılandırıldığından emin olun.|  
|Encodermessageversionuyuşmazlığı|Belirtilen giden iletinin ileti sürümü belirtilen kodlayıcı ile eşleşmiyor. Bağlamanın, iletiyle aynı sürümle yapılandırıldığından emin olun.|  
|Extracontensresentinfaultdetail|Hata ayrıntısı öğesinde ek genişletilebilir biçimlendirme dili içerik var. Yalnızca bir öğeye izin verilir.|  
|FilterBadTableType|Filtre için oluşturulan IMessageFilterTable, MessageFilterTable olamaz veya MessageFilterTable 'dan türetilmiş olamaz.|  
|Filtertableınvalidforlookup|MessageFilterTable durumu bozuk. İstenen arama gerçekleştirilemiyor.|  
|MandatoryHeaderNotUnderstood|Bir veya daha fazla gerekli basit nesne erişim Protokolü üst bilgi bloğu anlaşılmadı.|  
|MessageBodyIsStream|İleti gövdesi bir akıştır.|  
|Messagebodyısunknown|İleti gövdesinin biçimi bilinmiyor.|  
|Messagebodyreaderınvalidreadstate|İleti gövdesi okuyucusunun belirtilen ReadState 'i tüketilemiyor.|  
|Messagebir Codingnotsupported|Metin iletisi biçiminde kullanılan belirtilen metin kodlaması desteklenmiyor.|  
|Missingmessageıd|İstek Iletisinde bir MessageID üst bilgisi eksik. Bir yanıt ilişkilendirilmesi için MessageID üst bilgisi gereklidir.|  
|Çoğulmessageheaders|Belirtilen ad ve ad alanına sahip birden çok üstbilgi bulundu.|  
|Multiplemessageheaderswıaktör|Belirtilen ad, ad alanı ve rol ile birden çok üstbilgi bulundu.|  
|MultipleRelatesToHeaders|Belirtilen ilişkiye sahip birden fazla RelatesTo üst bilgisi bulundu. Her ilişki için yalnızca birine izin verilir.|  
|QueryFunctionTypeNotSupported|IXsltContextFunction için belirtilen dönüş türü desteklenmiyor.|  
|QueryIteratorOutOfScope|XPathNodeIterator geçersiz kılındı. Ixsltcontextfunctions 'a bağımsız değişken olarak geçirilen Xpathnodeıterators yalnızca işlev içinde geçerlidir. Bunlar daha sonra kullanılmak üzere veya işlev tarafından döndürülen önbelleğe alınamaz.|  
|QueryVariableNull|IXsltContextVariable metotları null döndüremez.|  
|QueryVariableTypeNotSupported|Belirtilen IXsltContextVariable türü desteklenmiyor.|  
|ReceiveShutdownReturnedMessage|Kanal, kapatılırken belirtilen eyleme sahip beklenmeyen bir giriş iletisi aldı. Daha fazla giriş iletisi beklemiyorsanız kanalı kapatın.|  
|Xmlbufferınınvalidstate|Bir iç hata oluştu. XML arabelleğinin durumu nedeniyle işlem gerçekleştirilemiyor.|  
|Xmlbufferquotaaşıldı|Genişletilebilir biçimlendirme dili içeriğini arabelleğe almak için gereken boyut, arabellek kotasını aştı.|
