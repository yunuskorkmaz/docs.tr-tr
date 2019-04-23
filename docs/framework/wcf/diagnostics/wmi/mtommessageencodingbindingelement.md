---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978178"
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
  
### <a name="encoding"></a>Encoding  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesi.  
  
### <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 İleti sayısını tanımlayan bir tamsayı yeni okuyucu ayırmadan aynı anda okuyabilirsiniz.  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 İleti sayısını tanımlayan bir tamsayı, yeni yazıcı ayırmadan aynı anda gönderilebilecek.  
  
### <a name="readerquotas"></a>ReaderQuotas  
 Veri türü: XmlDictionaryReaderQuotas  
  
 Erişim türü: salt okunur  
  
 Okuyucular kotalar.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
