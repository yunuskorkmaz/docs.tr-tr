---
description: 'Hakkında daha fazla bilgi edinin: TextMessageEncodingBindingElement'
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 9848f1660642f92c4bce3542fbd404f463b8c84d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757351"
---
# <a name="textmessageencodingbindingelement"></a>TextMessageEncodingBindingElement

TextMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntax  
  
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

 TextMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="encoding"></a>Encoding  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlaması.  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.  
  
### <a name="readerquotas"></a>ReaderQuotas  

 Veri türü: XmlDictionaryReaderQuotas  
  
 Erişim türü: salt okunurdur  
  
 Okuyucuların kotaları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
