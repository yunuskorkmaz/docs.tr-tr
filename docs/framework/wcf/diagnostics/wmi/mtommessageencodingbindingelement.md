---
description: 'Hakkında daha fazla bilgi edinin: MtomMessageEncodingBindingElement'
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: f06e3d7266c4f7e6f9b4639f7d82941cbabb5dd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803145"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement

MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntax  
  
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

 MtomMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 MtomMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
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

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
