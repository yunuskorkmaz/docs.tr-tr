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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1517d686c50923f5599e33436e0ad6126e8be140
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923150"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread Arabirimi
Bir işlemdeki bir iş parçacığını temsil eder. Bir `ICorDebugThread` örneğin yaşam süresi, temsil ettiği iş parçacığının ömrü ile aynıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Bu yöntem uygulanmadı. Onu kullanmayın.|  
|[CreateEval Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Bu `ICorDebugThread`, üzerinde çalışan bir ıcorınkıt geval nesnesi oluşturur.|  
|[CreateStepper Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Bu `ICorDebugThread`, içindeki etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.|  
|[EnumerateChains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Bu `ICorDebugThread`, içindeki tüm yığın zincirlerini Içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır.|  
|[GetActiveChain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Bu `ICorDebugThread`, üzerinde etkin ıcordebugzincirine bir arabirim işaretçisi alır.|  
|[GetActiveFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Bunun `ICorDebugThread`üzerinde etkin ICorDebugFrame 'e bir arabirim işaretçisi alır.|  
|[GetAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Şu anda yürütülmekte olan uygulama etki alanına `ICorDebugThread` bir arabirim işaretçisi alır.|  
|[GetCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.|  
|[GetDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Bunun `ICorDebugThread`geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır.|  
|[GetHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Bu `ICorDebugThread`öğesinin etkin bölümü için geçerli tanıtıcıyı alır.|  
|[GetID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Bu `ICorDebugThread`öğesinin etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Bu `ICorDebugThread` işlemin bir parçasını oluşturan işlem için bir arabirim işaretçisi alır.|  
|[GetRegisterSet Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Bu `ICorDebugThread`ile ilişkili kayıt kümesine bir arabirim işaretçisi alır.|  
|[GetUserState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Bunun `ICorDebugThread`geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır.|  
|[SetDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|`CorDebugThreadState` Bunun`ICorDebugThread`hata ayıklama durumunu tanımlayan değerlerin bit düzeyinde birleşimini ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
