---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 03a33f01fe6b6f75e81749c96c31770009350b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486569"
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 BinaryMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 BinaryMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir.  
  
## <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.  
  
## <a name="maxsessionsize"></a>maxSessionSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Kodlama için kullanılan arabelleğin bayt cinsinden boyutu belirten bir değer.  
  
## <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 Veri türü: XmlDictionaryReaderQuotas  
  
 Erişim türüne: salt okunur  
  
 Okuyucu kotaları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
