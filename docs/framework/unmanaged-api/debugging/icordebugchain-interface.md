---
title: Icordebugchain Interface1
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
ms.openlocfilehash: 32889a8e8867fc42b48413463095dda423f26b85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409847"
---
# <a name="icordebugchain-interface1"></a>Icordebugchain Interface1
Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateFrames Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|En son çerçeve ile başlayarak zincirde tüm yönetilen yığın çerçeveleri içeren bir numaralandırıcı alır.|  
|[GetActiveFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Etkin alır (yani, en son) zinciri çerçevesi.|  
|[GetCallee Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Bu zincir tarafından çağrıldı zinciri alır.|  
|[GetCaller Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Bu zincir adlı zinciri alır.|  
|[GetContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Henüz uygulanmadı.|  
|[GetNext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Çerçeve sonraki zincirine iş parçacığı alır.|  
|[GetPrevious Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Çerçeve önceki zincirine iş parçacığı alır.|  
|[GetReason Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Bu arama zincirini genesis nedeni alır.|  
|[GetRegisterSet Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Etkin bir parçası bu zincirinin ayarlamak kayıt alır.|  
|[GetStackRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Yığın kesiminin adres aralığı için bu zincirini alır.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Bu çağrı zinciri fiziksel iş parçacığı parçası alır.|  
|[IsManaged Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Yönetilen kod bu zincirini çalışır durumda olup olmadığını belirten bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın çerçeveleri zincirindeki bitişik yığın alanı kaplar ve aynı iş parçacığı bağlam paylaşın. Bir zincir ya da yönetilen veya yönetilmeyen kod zincirleri temsil edebilir. Boş bir `ICorDebugChain` örneği bir yönetilmeyen kod zinciri temsil eder.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
