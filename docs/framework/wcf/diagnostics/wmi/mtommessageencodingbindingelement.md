---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: b4d8503543c93d0112fc39e4b2dba5434bc56472
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237410"
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
