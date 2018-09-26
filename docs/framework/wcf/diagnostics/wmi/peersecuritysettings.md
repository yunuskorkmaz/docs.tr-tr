---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
ms.openlocfilehash: c74ee82d7aa3a23f0ee6a69185ad45857c31bb0b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087885"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
