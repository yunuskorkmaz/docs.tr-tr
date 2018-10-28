---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 49a640a666131491366646d6d486d25a515e35bf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185712"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 MtomMessageEncodingBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 MtomMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
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
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
