---
title: Hizmet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd784b470810e16b86ba7537b1f45681ac3e1ed1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="service"></a>Hizmet
Hizmet  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 Hizmet sınıfı, herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 Hizmet sınıfı, aşağıdaki özelliklere sahiptir:  
  
### <a name="baseaddresses"></a>BaseAddresses  
 Veri türü: dize dizisi  
  
 Erişim türüne: salt okunur  
  
 Hizmet tarafından kullanılan temel adres.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: davranış dizisi  
  
 Erişim türüne: salt okunur  
  
 Bu hizmetle ilişkilendirilen davranışlar.  
  
### <a name="configurationname"></a>ConfigurationName  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Hizmetinin performans sayaçları örneğinin örnek adı.  
  
### <a name="distinguishedname"></a>DistinguishedName  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Adresteki hizmet adı.  
  
### <a name="extensions"></a>Uzantıları  
 Veri türü: dize dizisi  
  
 Erişim türüne: salt okunur  
  
 Hizmet örneği uzantıları için örnek bağlamı.  
  
### <a name="metadata"></a>Meta Veriler  
 Veri türü: dize dizisi  
  
 Erişim türüne: salt okunur  
  
 Hizmet meta veri ayarları.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bu hizmetin benzersiz adı.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Hizmet ad alanı.  
  
### <a name="opened"></a>Açılan  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Hizmetin açıldığı zaman.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 Veri türü: kanal dizisi  
  
 Erişim türüne: salt okunur  
  
 Hizmet örneğinden giden kanallar.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Hizmeti barındıran işlemin işlem kimliği.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|
