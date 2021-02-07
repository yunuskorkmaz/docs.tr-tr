---
description: 'Daha fazla bilgi edinin: bağlama'
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 36887a9296bfafd0790105e7f4d513efc3009bf8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757793"
---
# <a name="binding"></a>Bağlama

WMI bağlama  
  
## <a name="syntax"></a>Syntax  
  
```csharp
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

 Bağlama sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 Bağlama sınıfı aşağıdaki özelliklere sahiptir.  
  
### <a name="bindingelements"></a>BindingElements  

 Veri türü: BindingElement dizisi  
  
 Erişim türü: salt okunurdur  
  
 Bağlama tarafından uygulanan bağlama öğelerinin koleksiyonu.  
  
### <a name="closetimeout"></a>CloseTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bir kapatma işleminin tamamlanabilmesi için girilen zaman aralığı.  
  
### <a name="name"></a>Name  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bağlamanın adı.  
  
### <a name="namespace"></a>Ad Alanı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bağlamanın XML ad alanı.  
  
### <a name="opentimeout"></a>OpenTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bir açık işlemin tamamlanabilmesi için girilen zaman aralığı.  
  
### <a name="receivetimeout"></a>ReceiveTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Alma işleminin tamamlanabilmesi için girilen zaman aralığı.  
  
### <a name="scheme"></a>Düzen  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bağlama tarafından oluşturulan kanal ve dinleyici fabrikaları tarafından kullanılan URI taşıma düzeni.  
  
### <a name="sendtimeout"></a>SendTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Gönderme işleminin tamamlanabilmesi için girilen zaman aralığı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
