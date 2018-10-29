---
title: Hizmet
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196914"
---
# <a name="service"></a>Hizmet
Hizmet  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Hizmet sınıfı, herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 Hizmet sınıfı, aşağıdaki özelliklere sahiptir:  
  
### <a name="baseaddresses"></a>BaseAddresses  
 Veri türü: dize dizisi  
  
 Erişim türü: salt okunur  
  
 Hizmet tarafından kullanılan tabanı.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: davranışı dizi  
  
 Erişim türü: salt okunur  
  
 Bu hizmetle ilişkili davranışlar.  
  
### <a name="configurationname"></a>ConfigurationName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Performans sayaçlarını hizmetin örneğini örnek adı.  
  
### <a name="distinguishedname"></a>DistinguishedName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Adresten hizmet adı.  
  
### <a name="extensions"></a>Uzantıları  
 Veri türü: dize dizisi  
  
 Erişim türü: salt okunur  
  
 Hizmeti örneğinin uzantıları için örnek bağlamı.  
  
### <a name="metadata"></a>Meta Veriler  
 Veri türü: dize dizisi  
  
 Erişim türü: salt okunur  
  
 Hizmet meta verilerini ayarlar.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bu hizmet benzersiz adı.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Hizmet ad alanı.  
  
### <a name="opened"></a>Açılan  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Hizmet açıldığı zaman.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 Veri türü: kanal dizisi  
  
 Erişim türü: salt okunur  
  
 Hizmeti örneğinin giden kanallar.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Hizmet barındıran işlemin işlem kimliği.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|
