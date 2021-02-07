---
description: 'Daha fazla bilgi edinin: hizmet'
title: Hizmet
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: e66f9a23f8c182327899904c26ff6a6368b9bdc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715632"
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
  
### <a name="metadata"></a>Meta veri  

 Veri türü: dize dizisi  
  
 Erişim türü: salt okunurdur  
  
 Hizmet meta verileri ayarları.  
  
### <a name="name"></a>Name  

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
