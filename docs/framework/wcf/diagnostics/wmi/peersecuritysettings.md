---
description: 'Daha fazla bilgi edinin: PeerSecuritySettings'
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: a8b5b8c88e71cb46110fa35186599c0f9c366d17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803015"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings

PeerSecuritySettings  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 PeerSecuritySettings sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="mode"></a>Mod  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bağlama ile yapılandırılan bir uç nokta tarafından ileti düzeyi ve aktarım düzeyi güvenlik kullanılıp kullanılmayacağını belirtir.  
  
### <a name="transport"></a>Aktarım  

 Veri türü: PeerTransportSecuritySettings  
  
 Erişim türü: salt okunurdur  
  
 Taşıma güvenlik ayarları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.PeerSecuritySettings>
