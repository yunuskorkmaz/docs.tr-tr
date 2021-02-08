---
description: 'Daha fazla bilgi edinin: MsmqTransportBindingElement'
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 4b6f363d979972c6ff0a2a378906feeece2ff6b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803158"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement

MsmqTransportBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 MsmqTransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="maxpoolsize"></a>MaxPoolSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 İç MSMQ ileti nesneleri içeren havuzun en büyük boyutu.  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlamanın kullandığı sıraya alınmış iletişim kanalı aktarımını gösteren bir numaralandırma değeri.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Sıra adreslerinin Active Directory kullanılarak dönüştürülmesi gerekip gerekmediğini belirten bir Boole değeri döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
