---
title: Icordebugchain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain
helpviewer_keywords: ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f964b5390e601b518acad44dd6fd170399ff0af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchain-interface1"></a>Icordebugchain Interface1
Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateFrames yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|En son çerçeve ile başlayarak zincirde tüm yönetilen yığın çerçeveleri içeren bir numaralandırıcı alır.|  
|[GetActiveFrame yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Etkin alır (yani, en son) zinciri çerçevesi.|  
|[GetCallee yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Bu zincir tarafından çağrıldı zinciri alır.|  
|[GetCaller yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Bu zincir adlı zinciri alır.|  
|[GetContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Henüz uygulanmadı.|  
|[GetNext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Çerçeve sonraki zincirine iş parçacığı alır.|  
|[GetPrevious yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Çerçeve önceki zincirine iş parçacığı alır.|  
|[GetReason yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Bu arama zincirini genesis nedeni alır.|  
|[GetRegisterSet yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Etkin bir parçası bu zincirinin ayarlamak kayıt alır.|  
|[GetStackRange yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Yığın kesiminin adres aralığı için bu zincirini alır.|  
|[GetThread yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Bu çağrı zinciri fiziksel iş parçacığı parçası alır.|  
|[Ismanaged yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Yönetilen kod bu zincirini çalışır durumda olup olmadığını belirten bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın çerçeveleri zincirindeki bitişik yığın alanı kaplar ve aynı iş parçacığı bağlam paylaşın. Bir zincir ya da yönetilen veya yönetilmeyen kod zincirleri temsil edebilir. Boş bir `ICorDebugChain` örneği bir yönetilmeyen kod zinciri temsil eder.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
