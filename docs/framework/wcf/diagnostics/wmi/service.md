---
title: Hizmet
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: aa4eecbcc8a2ef818cd99d777b0e3c2f1f222e46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273288"
---
# <a name="service"></a>Hizmet

Hizmet  
  
## <a name="syntax"></a>Syntax  
  
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

 Hizmet sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 Hizmet sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="baseaddresses"></a>BaseAddresses  

 Veri türü: dize dizisi  
  
 Erişim türü: salt okunurdur  
  
 Hizmet tarafından kullanılan taban adresler.  
  
### <a name="behaviors"></a>Davranışlar  

 Veri türü: davranış dizisi  
  
 Erişim türü: salt okunurdur  
  
 Bu hizmetle ilişkilendirilen davranışlar.  
  
### <a name="configurationname"></a>ConfigurationName  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin performans sayaçları örneğinin örnek adı.  
  
### <a name="distinguishedname"></a>DistinguishedName 'dir  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Adreste hizmet adı.  
  
### <a name="extensions"></a>Uzantıları  

 Veri türü: dize dizisi  
  
 Erişim türü: salt okunurdur  
  
 Hizmet örneği uzantılarının örnek bağlamları.  
  
### <a name="metadata"></a>Meta Veriler  

 Veri türü: dize dizisi  
  
 Erişim türü: salt okunurdur  
  
 Hizmet meta verileri ayarları.  
  
### <a name="name"></a>Adı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu hizmetin benzersiz adı.  
  
### <a name="namespace"></a>Ad Alanı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin ad alanı.  
  
### <a name="opened"></a>Makta  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin açıldığı zaman.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  

 Veri türü: Kanal dizisi  
  
 Erişim türü: salt okunurdur  
  
 Hizmet örneğinden giden kanallar.  
  
### <a name="processid"></a>Işlem  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Hizmeti barındıran işlemin işlem kimliği.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|
