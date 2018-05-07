---
title: Icordebugeval Interface1
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
ms.openlocfilehash: 3ceda938798ba03a9f178776c4cd9439456182c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval-interface1"></a>Icordebugeval Interface1
Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Bu hesaplama durdurur `ICorDebugEval` nesne gerçekleştirmekte.|  
|[CallFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Belirtilen işlev çağrısı ayarlar. (.NET Framework sürüm 2.0 artık kullanılmıyor; kullanın [Icordebugeval2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) yerine.)|  
|[CreateValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Bir arabirim işaretçisi ile başlangıç değeri sıfır ya da null olarak belirtilen tür için bir "ICorDebugValue" nesneyi alır. (.NET Framework 2. 0 ' artık kullanılmıyor; kullanın [Icordebugeval2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) yerine.)|  
|[GetResult Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Bir arabirim işaretçisi alır bir `ICorDebugValue` değerlendirme sonuçlarını içerir.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Arabirim işaretçisi "nereye bu değerlendirmeyi yürütüyor veya yürütecek Icordebugthread için" alır.|  
|[IsActive Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Gösteren bir değer alır olup olmadığını bu `ICorDebugEval` nesne şu anda yürütülmekte.|  
|[NewArray Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Belirtilen öğe türü ve boyutları yeni bir dizi ayırır. (.NET Framework 2. 0 ' artık kullanılmıyor; kullanın [Icordebugeval2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) yerine.)|  
|[NewObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Yeni bir nesne örneği ayırır ve belirtilen Oluşturucusu yöntemini çağırır. (.NET Framework 2. 0 ' artık kullanılmıyor; kullanın [Icordebugeval2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) yerine.)|  
|[NewObjectNoConstructor Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Yeni bir nesne örneği belirtilen türde bir oluşturucu yöntemi çağrı girişimi olmadan ayırır. (.NET Framework 2. 0 ' artık kullanılmıyor; kullanın [Icordebugeval2::newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) yerine.)|  
|[NewString Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Yeni bir dize nesnesi belirtilen içeriğiyle ayırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugEval` nesnesi değerlendirmesini gerçekleştirmek için kullanılan belirli bir iş parçacığı bağlamında oluşturulur. Tüm nesneleri ve belirli bir hesaplanmasında kullanılan türleri aynı uygulama etki alanında bulunmalıdır. Bu uygulama etki alanı iş parçacığının geçerli uygulama etki alanıyla aynı olması gerekmez. Değerlendirmeleri iç içe.  
  
 Değerlendirme 's işlemleri kadar hata ayıklayıcı çağrıları tamamlamayın [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)ve ardından alan bir [Icordebugmanagedcallback::evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) geri çağırma. Değerlendirme işlevi çalıştırmak başka bir iş parçacığı vermeden kullanmanız gerekiyorsa, kullanarak iş parçacıklarını askıya alma [Icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) veya [Icordebugcontroller::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)çağırmadan önce [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Değerlendirme sürdüğünden, kullanıcı kodu çalıştığından sınıfı yükler ve kesme noktaları da dahil olmak üzere tüm hata ayıklama olaylar gerçekleşebilir. Hata ayıklayıcı bu olayların normal olarak geri çağırmaları alır. Değerlendirme durumunu denetleme normal program durumunun bir parçası olarak görülür. Yığın zinciri olacak bir `CHAIN_FUNC_EVAL` zinciri ("CorDebugStepReason" numaralandırması bakın ve [Icordebugchain::getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) yöntemi). Tam hata ayıklayıcı API normal olarak çalışmaya devam eder.  
  
 Kilitlenen veya sonsuz bir döngü durum oluşursa, kullanıcı kodu hiçbir zaman tamamlanabilir. Böyle bir durumda çağırmalısınız [Icordebugeval::Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) önce programı'na devam ediliyor.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
    
    
    
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
