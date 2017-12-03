---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
