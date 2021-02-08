---
description: ': ICLROnEventManager arabirimi hakkında daha fazla bilgi edinin'
title: ICLROnEventManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 7a9c0beec5083bc93f5361bb0e701da5beeedea2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789833"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager Arabirimi

Ana bilgisayarın ortak dil çalışma zamanı (CLR) olayları için geri çağırmaları kaydetmesine ve kaydını kaydetmesine izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[RegisterActionOnEvent Yöntemi](iclroneventmanager-registeractiononevent-method.md)|Belirtilen olay için bir geri çağırma işaretçisi kaydeder.|  
|[UnregisterActionOnEvent Yöntemi](iclroneventmanager-unregisteractiononevent-method.md)|Belirtilen olay için önceden kaydedilmiş bir geri çağırma işaretçisinin kaydını siler.|  
  
## <a name="remarks"></a>Açıklamalar  

 Olay geri çağırmaları kaydetmek ve kaydını silmek için, ana bilgisayar `ICLROnEventManager` [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırarak öğesine bir başvuru alır.  
  
> [!NOTE]
> [EClrEvent](eclrevent-enumeration.md) tarafından tanımlanan olaylar birden çok kez tetiklenebilir ve farklı iş PARÇACıKLARıNDAN clr 'nin kaldırılmasına veya devre dışı bırakılmasına işaret edebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrEvent Numaralandırması](eclrevent-enumeration.md)
- [IActionOnCLREvent Arabirimi](iactiononclrevent-interface.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
