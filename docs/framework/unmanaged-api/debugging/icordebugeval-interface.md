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
ms.openlocfilehash: 745917af176de47999737c87833c23df9c75ea7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080871"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval Arabirimi

Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Bu hesaplama durdurur `ICorDebugEval` nesne şu anda gerçekleştiriyor.|  
|[CallFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Belirtilen işlev çağrısı ayarlar. (.NET Framework 2.0 sürümünde artık kullanılmıyor; kullanma [Icordebugeval2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) yerine.)|  
|[CreateValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Bir arabirim işaretçisi için bir "ICorDebugValue" nesne belirtilen türe ait bir başlangıç değeri sıfır ya da null ile alır. (.NET Framework 2.0 sürümünde artık kullanılmıyor; kullanma [Icordebugeval2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) yerine.)|  
|[GetResult Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Bir arabirim işaretçisi alır bir `ICorDebugValue` , değerlendirme sonuçlarını içerir.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|"Bu değerlendirme burada yürütülüyor veya çalıştırır Icordebugthread için" bir arabirim işaretçisi alır.|  
|[IsActive Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Belirten bir değer alır olup bu `ICorDebugEval` nesne şu anda yürütülüyor.|  
|[NewArray Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Belirtilen öğe türü ve boyut yeni bir dizi ayırır. (.NET Framework 2.0 sürümünde artık kullanılmıyor; kullanma [Icordebugeval2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) yerine.)|  
|[NewObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Yeni bir nesne örneğini tahsis eder ve belirtilen yapıcı yöntemini çağırır. (.NET Framework 2.0 sürümünde artık kullanılmıyor; kullanma [Icordebugeval2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) yerine.)|  
|[NewObjectNoConstructor Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Yeni bir nesne örneği belirtilen türe ait bir oluşturucu yöntemini çağırma girişimi olmadan ayırır. (.NET Framework 2.0 sürümünde artık kullanılmıyor; kullanma [Icordebugeval2::newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) yerine.)|  
|[NewString Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Yeni bir dize nesnesi belirtilen içeriği ile ayırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugEval` nesnesi değerlendirmelerini gerçekleştirmek için kullanılan belirli bir iş parçacığının bağlamında oluşturulur. Tüm nesneleri ve belirli bir veriyi değerlendirmede kullanılan türler aynı uygulama etki alanında bulunmalıdır. Bu uygulama etki alanı iş parçacığının geçerli uygulama etki alanı ile aynı olması gerekmez. Değerlendirmeleri yuvalanabilir.  
  
 Değerlendirme'nın operations kadar hata ayıklayıcı çağrıları tamamlamayın [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)ve ardından alan bir [Icordebugmanagedcallback::evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) geri çağırma. Başka iş parçacıklarının çalışmasına izin verilmeden değerlendirme işlevlerini kullanmanız gerekiyorsa, kullanarak iş parçacıklarını askıya almasının [Icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) veya [Icordebugcontroller::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)çağırmadan önce [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Kullanıcı kodu değerlendirme devam ederken çalıştığından, sınıf yükler ve kesme noktaları da dahil olmak üzere herhangi bir hata ayıklama olaylarını oluşabilir. Hata ayıklayıcı bu olaylar için normal olarak geri çağırmaları alır. Değerlendirme durumu normal program durumunu incelenmesi bir parçası olarak görülür. Yığın zincirinin olacak bir `CHAIN_FUNC_EVAL` zinciri ("CorDebugStepReason" sabit bakın ve [Icordebugchain::getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) yöntemi). Tam hata ayıklayıcı API normal şekilde çalışmaya devam eder.  
  
 Kilitlenen veya sonsuz bir döngü durum ortaya çıkarsa, kullanıcı kodu asla tamamlanabilir. Böyle bir durumda çağırmalısınız [Icordebugeval::Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) önce program sürdürülüyor.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
