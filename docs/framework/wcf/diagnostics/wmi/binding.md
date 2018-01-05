---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6553d1e1c030a30eed74ff81d3e07e28a9f25b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="binding"></a>Bağlama
WMI bağlama  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Bağlama sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 Bağlama sınıfı aşağıdaki özelliklere sahiptir.  
  
### <a name="bindingelements"></a>BindingElements  
 Veri türü: BindingElement dizisi  
  
 Erişim türüne: salt okunur  
  
 Bağlama tarafından uygulanan bağlama öğeleri koleksiyonu.  
  
### <a name="closetimeout"></a>closeTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Bir kapatma işlemi tamamlamak sağlanan zaman aralığı.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bağlama adı.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 XML ad alanı bağlama.  
  
### <a name="opentimeout"></a>openTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Bir açık işleminin tamamlanması için sağlanan zaman aralığı.  
  
### <a name="receivetimeout"></a>receiveTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Bir alma işleminin tamamlanması için sağlanan zaman aralığı.  
  
### <a name="scheme"></a>Düzen  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bağlama tarafından oluşturulan kanal ve dinleyici üreteçleri tarafından kullanılan URI aktarma düzenini.  
  
### <a name="sendtimeout"></a>sendTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Bir gönderme işleminin tamamlanması için sağlanan zaman aralığı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>
