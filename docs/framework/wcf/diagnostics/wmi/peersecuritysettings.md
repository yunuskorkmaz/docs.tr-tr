---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 92aca4c790607de91314aacf6414d0dfacea9a9f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193168"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 PeerSecuritySettings sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="mode"></a>Mod  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İleti düzeyi olup olmadığını ve aktarım düzeyi güvenlik bağlama ile yapılandırılan bir uç nokta tarafından kullanılır.  
  
### <a name="transport"></a>Taşıma  
 Veri türü: PeerTransportSecuritySettings  
  
 Erişim türü: salt okunur  
  
 Taşıma güvenliği ayarları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.PeerSecuritySettings>
