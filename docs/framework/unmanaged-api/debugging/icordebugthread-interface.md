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
ms.openlocfilehash: b227b374021136e78f7f061d235eb18eca5b9515
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791482"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread Arabirimi
Bir işlemdeki bir iş parçacığını temsil eder. Bir `ICorDebugThread` örneğinin kullanım ömrü, temsil ettiği iş parçacığının yaşam süresi ile aynıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](icordebugthread-clearcurrentexception-method.md)|Bu yöntem uygulanmadı. Onu kullanmayın.|  
|[CreateEval Yöntemi](icordebugthread-createeval-method.md)|Bu `ICorDebugThread`çalışan bir ıcorınkıt Geval nesnesi oluşturur.|  
|[CreateStepper Yöntemi](icordebugthread-createstepper-method.md)|Bu `ICorDebugThread`etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.|  
|[EnumerateChains Yöntemi](icordebugthread-enumeratechains-method.md)|Bu `ICorDebugThread`tüm yığın zincirlerini içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır.|  
|[GetActiveChain Yöntemi](icordebugthread-getactivechain-method.md)|Bu `ICorDebugThread`etkin ıcordebugzincirine yönelik bir arabirim işaretçisi alır.|  
|[GetActiveFrame Yöntemi](icordebugthread-getactiveframe-method.md)|Bu `ICorDebugThread`etkin ICorDebugFrame 'e bir arabirim işaretçisi alır.|  
|[GetAppDomain Yöntemi](icordebugthread-getappdomain-method.md)|Bu `ICorDebugThread` Şu anda yürütüldüğü uygulama etki alanına bir arabirim işaretçisi alır.|  
|[GetCurrentException Yöntemi](icordebugthread-getcurrentexception-method.md)|Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.|  
|[GetDebugState Yöntemi](icordebugthread-getdebugstate-method.md)|Bu `ICorDebugThread`geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır.|  
|[GetHandle Yöntemi](icordebugthread-gethandle-method.md)|Bu `ICorDebugThread`etkin bölümü için geçerli tanıtıcıyı alır.|  
|[GetID Yöntemi](icordebugthread-getid-method.md)|Bu `ICorDebugThread`etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.|  
|[GetObject Yöntemi](icordebugthread-getobject-method.md)|Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](icordebugthread-getprocess-method.md)|Bu `ICorDebugThread` bir parçasını oluşturan işlem için bir arabirim işaretçisi alır.|  
|[GetRegisterSet Yöntemi](icordebugthread-getregisterset-method.md)|Bu `ICorDebugThread`ilişkili kayıt kümesine bir arabirim işaretçisi alır.|  
|[GetUserState Yöntemi](icordebugthread-getuserstate-method.md)|Bu `ICorDebugThread`geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır.|  
|[SetDebugState Yöntemi](icordebugthread-setdebugstate-method.md)|Bu `ICorDebugThread`hata ayıklama durumunu tanımlayan `CorDebugThreadState` değerlerinin bit düzeyinde birleşimini ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
