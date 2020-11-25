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
ms.openlocfilehash: 5d8fd79b242f2b88b82c5c3d78dfe45d80f1194f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729791"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval Arabirimi

Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](icordebugeval-abort-method.md)|Bu `ICorDebugEval` nesnenin şu anda gerçekleştirdiği hesaplamayı iptal eder.|  
|[CallFunction Yöntemi](icordebugeval-callfunction-method.md)|Belirtilen işleve bir çağrı kurar. (.NET Framework sürüm 2,0 ' de kullanımdan kalktı; bunun yerine [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) kullanın.)|  
|[CreateValue Yöntemi](icordebugeval-createvalue-method.md)|Belirtilen türde bir "ICorDebugValue" nesnesi için sıfır veya null değeri olan bir arabirim işaretçisi alır. (.NET Framework 2,0 ' de kullanılmıyor; bunun yerine [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) kullanın.)|  
|[GetResult Yöntemi](icordebugeval-getresult-method.md)|Değerlendirmede oluşan sonuçları içeren bir arabirim işaretçisi alır `ICorDebugValue` .|  
|[GetThread Yöntemi](icordebugeval-getthread-method.md)|Bu değerlendirmenin yürütüldüğü veya yürütüleceği "ICorDebugThread" için bir arabirim işaretçisi alır.|  
|[IsActive Yöntemi](icordebugeval-isactive-method.md)|Bu nesnenin şu anda çalışıp çalışmadığını gösteren bir değer alır `ICorDebugEval` .|  
|[NewArray Yöntemi](icordebugeval-newarray-method.md)|Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır. (.NET Framework 2,0 ' de kullanılmıyor; bunun yerine [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) kullanın.)|  
|[NewObject Yöntemi](icordebugeval-newobject-method.md)|Yeni bir nesne örneği ayırır ve belirtilen Oluşturucu yöntemini çağırır. (.NET Framework 2,0 ' de kullanılmıyor; bunun yerine [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) kullanın.)|  
|[NewObjectNoConstructor Yöntemi](icordebugeval-newobjectnoconstructor-method.md)|Bir Oluşturucu yöntemini çağırmaya çalışmadan, belirtilen türün yeni bir nesne örneğini ayırır. (.NET Framework 2,0 ' de kullanılmıyor; bunun yerine [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) kullanın.)|  
|[NewString Yöntemi](icordebugeval-newstring-method.md)|Belirtilen içeriğe sahip yeni bir dize nesnesi ayırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir `ICorDebugEval` nesne, değerlendirmeleri gerçekleştirmek için kullanılan belirli bir iş parçacığının bağlamında oluşturulur. Belirli bir değerlendirmede kullanılan tüm nesneler ve türler aynı uygulama etki alanı içinde bulunmalıdır. Bu uygulama etki alanının, iş parçacığının geçerli uygulama etki alanıyla aynı olmaması gerekir. Değerlendirmeler iç içe olabilir.  
  
 Hata ayıklayıcı [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)öğesini çağırana kadar değerlendirmenin işlemleri tamamlanmaz ve sonra bir [ICorDebugManagedCallback:: evaltamamlanmamış](icordebugmanagedcallback-evalcomplete-method.md) geri çağırma alır. Değerlendirme işlevini diğer iş parçacıklarının çalışmasına izin vermeden kullanmanız gerekiyorsa, ICorDebugController: [: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) veya [ICorDebugController](icordebugcontroller-stop-method.md) :: Stop komutunu çağırmadan önce ICorDebugController:: [Continue](icordebugcontroller-continue-method.md)kullanarak iş parçacıklarını askıya alın.  
  
 Değerlendirme devam ederken Kullanıcı kodu çalıştığından, sınıf yüklemeleri ve kesme noktaları da dahil olmak üzere herhangi bir hata ayıklama olayı meydana gelebilir. Hata ayıklayıcı, bu olaylar için normal olarak geri çağırmaları alır. Değerlendirme durumu, normal program durumunun incelemesinin bir parçası olarak görünür. Yığın zinciri bir `CHAIN_FUNC_EVAL` zincir olacaktır ("CorDebugStepReason" sabit listesine ve [ıcordebugzincirine:: GetReason](icordebugchain-getreason-method.md) yöntemine bakın). Tam hata ayıklayıcı API 'SI normal şekilde çalışmaya devam edecektir.  
  
 Kilitli veya sonsuz döngü durumu oluşursa, Kullanıcı kodu hiç tamamlanmayabilir. Böyle bir durumda, programı devam ettirmeden önce [ıcorınkıımagegeval:: Abort](icordebugeval-abort-method.md) çağrısı yapmanız gerekir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
