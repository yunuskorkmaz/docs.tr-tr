---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 83fa879fbef94e2dc9c142dfb92a51a54a7b60cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486540"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 MtomMessageEncodingBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 MtomMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="encoding"></a>Kodlama  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bağlama iletilerde yayma için kullanılacak kodlama karakter kümesi.  
  
### <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Kaç tane iletileri tanımlayan bir tamsayı yeni okuyucu ayırmadan eşzamanlı olarak okuyabilirsiniz.  
  
### <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Kaç tane iletileri tanımlayan bir tamsayı yeni yazıcı ayırmadan aynı anda gönderilebilir.  
  
### <a name="readerquotas"></a>ReaderQuotas  
 Veri türü: XmlDictionaryReaderQuotas  
  
 Erişim türüne: salt okunur  
  
 Okuyucu kotaları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
