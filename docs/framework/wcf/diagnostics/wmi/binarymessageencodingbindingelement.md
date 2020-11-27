---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: eb174d12731d7f1bc78f4d709cf043daf2346bd2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269801"
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement

BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 BinaryMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 BinaryMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir.  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.  
  
## <a name="maxsessionsize"></a>MaxSessionSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Kodlama için kullanılan arabelleğin bayt cinsinden boyutunu belirten bir değer.  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.  
  
## <a name="readerquotas"></a>ReaderQuotas  

 Veri türü: XmlDictionaryReaderQuotas  
  
 Erişim türü: salt okunurdur  
  
 Okuyucuların kotaları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
