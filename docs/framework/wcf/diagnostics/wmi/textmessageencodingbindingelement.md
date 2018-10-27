---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 2371c38aebe2bd8d6da93d702801556fad986ef9
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452579"
---
# <a name="textmessageencodingbindingelement"></a>TextMessageEncodingBindingElement
TextMessageEncodingBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 TextMessageEncodingBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="encoding"></a>Kodlama  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesi.  
  
### <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.  
  
### <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.  
  
### <a name="readerquotas"></a>readerQuotas  
 Veri türü: XmlDictionaryReaderQuotas  
  
 Erişim türü: salt okunur  
  
 Okuyucular kotalar.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
