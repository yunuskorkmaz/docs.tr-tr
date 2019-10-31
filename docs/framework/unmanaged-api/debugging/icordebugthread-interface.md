---
title: ICorDebugThread Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: c7333f4210d0a2ec4ff71a0fac0ea00068fecc57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133504"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread Arabirimi
Bir işlemdeki bir iş parçacığını temsil eder. Bir `ICorDebugThread` örneğinin kullanım ömrü, temsil ettiği iş parçacığının yaşam süresi ile aynıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Bu yöntem uygulanmadı. Onu kullanmayın.|  
|[CreateEval Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Bu `ICorDebugThread`çalışan bir ıcorınkıt Geval nesnesi oluşturur.|  
|[CreateStepper Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Bu `ICorDebugThread`etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.|  
|[EnumerateChains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Bu `ICorDebugThread`tüm yığın zincirlerini içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır.|  
|[GetActiveChain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Bu `ICorDebugThread`etkin ıcordebugzincirine yönelik bir arabirim işaretçisi alır.|  
|[GetActiveFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Bu `ICorDebugThread`etkin ICorDebugFrame 'e bir arabirim işaretçisi alır.|  
|[GetAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Bu `ICorDebugThread` Şu anda yürütüldüğü uygulama etki alanına bir arabirim işaretçisi alır.|  
|[GetCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.|  
|[GetDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Bu `ICorDebugThread`geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır.|  
|[GetHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Bu `ICorDebugThread`etkin bölümü için geçerli tanıtıcıyı alır.|  
|[GetID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Bu `ICorDebugThread`etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Bu `ICorDebugThread` bir parçasını oluşturan işlem için bir arabirim işaretçisi alır.|  
|[GetRegisterSet Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Bu `ICorDebugThread`ilişkili kayıt kümesine bir arabirim işaretçisi alır.|  
|[GetUserState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Bu `ICorDebugThread`geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır.|  
|[SetDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Bu `ICorDebugThread`hata ayıklama durumunu tanımlayan `CorDebugThreadState` değerlerinin bit düzeyinde birleşimini ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
