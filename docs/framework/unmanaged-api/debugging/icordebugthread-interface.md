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
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379816"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread Arabirimi
Bir işlemdeki bir iş parçacığını temsil eder. Bir örneğin yaşam süresi, `ICorDebugThread` temsil ettiği iş parçacığının ömrü ile aynıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](icordebugthread-clearcurrentexception-method.md)|Bu yöntem uygulanmadı. Onu kullanmayın.|  
|[CreateEval Yöntemi](icordebugthread-createeval-method.md)|Bu, üzerinde çalışan bir ıcorınkıt Geval nesnesi oluşturur `ICorDebugThread` .|  
|[CreateStepper Yöntemi](icordebugthread-createstepper-method.md)|Bu, içindeki etkin çerçeve üzerinde Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur `ICorDebugThread` .|  
|[EnumerateChains Yöntemi](icordebugthread-enumeratechains-method.md)|Bu, içindeki tüm yığın zincirlerini içeren ICorDebugChainEnum numaralandırıcısı için bir arabirim işaretçisi alır `ICorDebugThread` .|  
|[GetActiveChain Yöntemi](icordebugthread-getactivechain-method.md)|Bu, üzerinde etkin ıcordebugzincirine bir arabirim işaretçisi alır `ICorDebugThread` .|  
|[GetActiveFrame Metodu](icordebugthread-getactiveframe-method.md)|Bunun üzerinde etkin ICorDebugFrame 'e bir arabirim işaretçisi alır `ICorDebugThread` .|  
|[GetAppDomain Yöntemi](icordebugthread-getappdomain-method.md)|Şu anda yürütülmekte olan uygulama etki alanına bir arabirim işaretçisi alır `ICorDebugThread` .|  
|[GetCurrentException Yöntemi](icordebugthread-getcurrentexception-method.md)|Yönetilen kod tarafından şu anda oluşturulan bir özel durumu temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.|  
|[GetDebugState Yöntemi](icordebugthread-getdebugstate-method.md)|Bunun geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değeri alır `ICorDebugThread` .|  
|[GetHandle Yöntemi](icordebugthread-gethandle-method.md)|Bu öğesinin etkin bölümü için geçerli tanıtıcıyı alır `ICorDebugThread` .|  
|[GetID Yöntemi](icordebugthread-getid-method.md)|Bu öğesinin etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır `ICorDebugThread` .|  
|[GetObject Metodu](icordebugthread-getobject-method.md)|Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](icordebugthread-getprocess-method.md)|Bu işlemin bir parçasını oluşturan işlem için bir arabirim işaretçisi alır `ICorDebugThread` .|  
|[GetRegisterSet Metodu](icordebugthread-getregisterset-method.md)|Bu ile ilişkili kayıt kümesine bir arabirim işaretçisi alır `ICorDebugThread` .|  
|[GetUserState Yöntemi](icordebugthread-getuserstate-method.md)|Bunun geçerli durumunu tanımlayan CorDebugUserState değerlerinin bit düzeyinde birleşimini alır `ICorDebugThread` .|  
|[SetDebugState Yöntemi](icordebugthread-setdebugstate-method.md)|`CorDebugThreadState`Bunun hata ayıklama durumunu tanımlayan değerlerin bit düzeyinde birleşimini ayarlar `ICorDebugThread` .|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
