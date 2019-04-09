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
ms.openlocfilehash: db322bbdc7293410968542d0d22c572edb87795a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184710"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread Arabirimi
Bir işlemdeki bir iş parçacığını temsil eder. Yaşam süresi bir `ICorDebugThread` örneğidir ömrü, temsil ettiği iş parçacığı ile aynı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Bu yöntem uygulanmadı. Onu kullanmayın.|  
|[CreateEval Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Bu, çalışan Icordebugeval nesne oluşturur `ICorDebugThread`.|  
|[CreateStepper Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Bu etkin çerçeveye üzerinden Adımlama izin veren bir ICorDebugStepper nesnesi oluşturur `ICorDebugThread`.|  
|[EnumerateChains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Bu yığın zincirlerini içeren bir Icordebugchainenum Numaralandırıcı için bir arabirim işaretçisi alır `ICorDebugThread`.|  
|[GetActiveChain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Bu etkin Icordebugchain için bir arabirim işaretçisi alır `ICorDebugThread`.|  
|[GetActiveFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Bu etkin Icordebugframe için bir arabirim işaretçisi alır `ICorDebugThread`.|  
|[GetAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Bu uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugThread` gerçekleştirmektedir.|  
|[GetCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Şu anda yönetilen kod tarafından oluşturulan bir özel durum temsil eden bir Icordebugvalue nesne için bir arabirim işaretçisi alır.|  
|[GetDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Bu, geçerli hata ayıklama durumunu açıklayan bir CorDebugThreadState değerini alır `ICorDebugThread`.|  
|[GetHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Bu, etkin parçası için geçerli bir tanıtıcı alır `ICorDebugThread`.|  
|[GetID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Bu etkin parçası geçerli işletim sistemi tanımlayıcısını alır `ICorDebugThread`.|  
|[GetObject Metodu](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Bu işlemi bir arabirim işaretçisi alır `ICorDebugThread` bir bölümünü oluşturur.|  
|[GetRegisterSet Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Bu ile ilişkilendirilen kayıt kümesi için bir arabirim işaretçisi alır `ICorDebugThread`.|  
|[GetUserState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Bu geçerli durumunu açıklayan CorDebugUserState değerlerinin bit tabanı bir bileşimine alır `ICorDebugThread`.|  
|[SetDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Bitsel bir birleşimi ayarlar `CorDebugThreadState` bu hata ayıklama durumunu açıklayan değerleri `ICorDebugThread`.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
