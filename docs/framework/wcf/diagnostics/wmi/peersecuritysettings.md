---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 2de417e4a4f5c6197551c1408da6907e2fa7c635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269008"
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
