---
title: ICorDebugChain Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01dded47fca26df11781153eb45693057a25ad01
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220714"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain Arabirimi

Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateFrames Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|En son çerçeve ile başlayan zincirindeki tüm yönetilen yığın çerçevesi içeren bir numaralandırıcı alır.|  
|[GetActiveFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Etkin alır (yani, en son) zincirindeki çerçeve.|  
|[GetCallee Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Bu zincir tarafından çağrıldı zinciri alır.|  
|[GetCaller Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Bu zincir denir zinciri alır.|  
|[GetContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Henüz uygulanmadı.|  
|[GetNext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Çerçeve sonraki zincirini iş parçacığı alır.|  
|[GetPrevious Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Çerçeve önceki zincirini iş parçacığı alır.|  
|[GetReason Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Bu çağrı zincirinin genesis nedenini alır.|  
|[GetRegisterSet Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Bu zincir etkin parçası için kaydı alır.|  
|[GetStackRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Yığın kesiminin adres aralığı için bu zincir alır.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Bu çağrı zinciri fiziksel iş parçacığı parçası alır.|  
|[IsManaged Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Bu zincir yönetilen kod çalışır durumda olup olmadığını gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın çerçevelerini zincirindeki, bitişik yığın alanı kaplayan ve aynı iş parçacığı ve içerik paylaşın. Zinciri ya da yönetilen veya yönetilmeyen koda zincirleri temsil edebilir. Boş bir `ICorDebugChain` örneği bir yönetilmeyen kod zincirini temsil eder.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
