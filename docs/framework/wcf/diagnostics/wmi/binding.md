---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149711"
---
# <a name="binding"></a>Bağlama
WMI bağlama  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 Bağlama sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 Bağlama sınıfı aşağıdaki özelliklere sahiptir.  
  
### <a name="bindingelements"></a>BindingElements  
 Veri türü: BindingElement dizi  
  
 Erişim türü: salt okunur  
  
 Bağlama tarafından uygulanan bağlama öğeleri koleksiyonu.  
  
### <a name="closetimeout"></a>closeTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Bir kapatma işlemi tamamlamak sağlanan zaman aralığı.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bağlama adı.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 XML ad alanı bağlama.  
  
### <a name="opentimeout"></a>opentimeout =  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Sağlanan bir açık bir işlemin tamamlanması zaman aralığı.  
  
### <a name="receivetimeout"></a>receiveTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Tamamlamak alma işlemi için belirtilen zaman aralığı.  
  
### <a name="scheme"></a>Düzen  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bağlama tarafından oluşturulan kanal ve dinleyici fabrikası tarafından kullanılan URI aktarma düzenini.  
  
### <a name="sendtimeout"></a>SendTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Tamamlamak için bir gönderme işlemi belirtilen zaman aralığı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>
