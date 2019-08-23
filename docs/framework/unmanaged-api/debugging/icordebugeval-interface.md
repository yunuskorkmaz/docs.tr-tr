---
title: ICorDebugEval Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd29067f819ba69305f7ae8620729cd443915a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931944"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval Arabirimi

Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Bu `ICorDebugEval` nesnenin şu anda gerçekleştirdiği hesaplamayı iptal eder.|  
|[CallFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Belirtilen işleve bir çağrı kurar. (.NET Framework sürüm 2,0 ' de kullanımdan kalktı; bunun yerine [ICorDebugEval2:: CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) kullanın.)|  
|[CreateValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Belirtilen türde bir "ICorDebugValue" nesnesi için sıfır veya null değeri olan bir arabirim işaretçisi alır. (.NET Framework 2,0 ' de kullanılmıyor; bunun yerine [ICorDebugEval2:: CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) kullanın.)|  
|[GetResult Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Değerlendirmede oluşan sonuçları içeren bir `ICorDebugValue` arabirim işaretçisi alır.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Bu değerlendirmenin yürütüldüğü veya yürütüleceği "ICorDebugThread" için bir arabirim işaretçisi alır.|  
|[IsActive Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Bu `ICorDebugEval` nesnenin şu anda çalışıp çalışmadığını gösteren bir değer alır.|  
|[NewArray Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır. (.NET Framework 2,0 ' de kullanılmıyor; bunun yerine [ICorDebugEval2:: NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) kullanın.)|  
|[NewObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Yeni bir nesne örneği ayırır ve belirtilen Oluşturucu yöntemini çağırır. (.NET Framework 2,0 ' de kullanılmıyor; bunun yerine [ICorDebugEval2:: NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) kullanın.)|  
|[NewObjectNoConstructor Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Bir Oluşturucu yöntemini çağırmaya çalışmadan, belirtilen türün yeni bir nesne örneğini ayırır. (.NET Framework 2,0 ' de kullanılmıyor; bunun yerine [ICorDebugEval2:: NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) kullanın.)|  
|[NewString Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Belirtilen içeriğe sahip yeni bir dize nesnesi ayırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugEval` nesne, değerlendirmeleri gerçekleştirmek için kullanılan belirli bir iş parçacığının bağlamında oluşturulur. Belirli bir değerlendirmede kullanılan tüm nesneler ve türler aynı uygulama etki alanı içinde bulunmalıdır. Bu uygulama etki alanının, iş parçacığının geçerli uygulama etki alanıyla aynı olmaması gerekir. Değerlendirmeler iç içe olabilir.  
  
 Hata ayıklayıcı [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)öğesini çağırana kadar değerlendirmenin işlemleri tamamlanmaz ve sonra bir [ICorDebugManagedCallback:: evaltamamlanmamış](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) geri çağırma alır. Değerlendirme işlevini diğer iş parçacıklarının çalışmasına izin vermeden kullanmanız gerekiyorsa, iş parçacıklarını [ICorDebugController:: SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) veya [ICorDebugController::](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md) komutunu çağırmadan [önce durdurun ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Değerlendirme devam ederken Kullanıcı kodu çalıştığından, sınıf yüklemeleri ve kesme noktaları da dahil olmak üzere herhangi bir hata ayıklama olayı meydana gelebilir. Hata ayıklayıcı, bu olaylar için normal olarak geri çağırmaları alır. Değerlendirme durumu, normal program durumunun incelemesinin bir parçası olarak görünür. Yığın zinciri bir `CHAIN_FUNC_EVAL` zincir olacaktır ("CorDebugStepReason" sabit listesine ve [ıcordebugzincirine:: GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) yöntemine bakın). Tam hata ayıklayıcı API 'SI normal şekilde çalışmaya devam edecektir.  
  
 Kilitli veya sonsuz döngü durumu oluşursa, Kullanıcı kodu hiç tamamlanmayabilir. Böyle bir durumda, programı devam ettirmeden önce [ıcorınkıımagegeval:: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) çağrısı yapmanız gerekir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
