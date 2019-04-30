---
title: ICorDebugStepper Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f83b9796bb692ce234a03c596387960bd879ebf3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763743"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper Arabirimi
Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Deactivate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Bu neden `ICorDebugStepper` aldığı son adım komutunu iptal etmek için.|  
|[IsActive Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Belirten bir değer alır olup bu `ICorDebugStepper` bir adımı yürütülüyor.|  
|[SetInterceptMask Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|İçine girdiğiniz kod türlerini belirten bir Cordebugıntercept değeri ayarlar.|  
|[SetRangeIL Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Belirten bir değeri ayarlar olmadığını çağrılar [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) aracılığıyla basamaklı yöntemin Microsoft Ara dili (MSIL) kodu veya yerel koda göre bağımsız değişken değerlerini geçirirsiniz.|  
|[SetUnmappedStopMask Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Yürütmeyi durdur eşlenmemiş kodun türünü belirten bir CorDebugUnmappedStop değeri ayarlar.|  
|[Step Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Bu neden olur `ICorDebugStepper` tek adımlı içeren kendi iş parçacığı aracılığıyla ve isteğe bağlı olarak için için iş parçacığının içinden çağıran işlevler aracılığıyla tek Adımlama devam edin.|  
|[StepOut Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Bu neden `ICorDebugStepper` içeren kendi iş parçacığı aracılığıyla tek adımlı ve tam olduğunda geçerli çerçeve arama çerçeveye denetimini döndürür.|  
|[StepRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Bu neden `ICorDebugStepper` isteğe bağlı olarak tek-adım içeren kendi iş parçacığı ve ne zaman döndürmek için son belirtilen aralıkların dışında kod ulaşır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugStepper` Arabirimi aşağıdaki amaçlara hizmet eder:  
  
- Verilen bir adım komut ve bu komutun tamamlanması arasında bir tanımlayıcı işlevi görür.  
  
- Bunu gerçekleştirilebilecek tüm Adımlama kapsüllemek için merkezi bir arabirim sağlar.  
  
- Erken bir atlama işlemi iptal etmek için bir yol sunar.  
  
 İş parçacığı başına birden fazla adımlayıcıdaki olabilir. Örneğin, bir işlevin üzerine erişilince bir kesme noktası isabet ve bu işlevin içindeki yeni bir atlama işlemi başlatmak kullanıcı isteyebilir. Bu durumu yönetmek nasıl belirlemek için hata ayıklayıcı kadar var. Hata ayıklayıcı özgün atlama işlemi iptal etmek veya iki işlem iç içe isteyebilirsiniz. `ICorDebugStepper` Arabirimi iki seçeneği destekler.  
  
 Ortak dil çalışma zamanı (CLR) arası iş parçacıklı, sıralanmış bir çağrı yaparsa Adımlayıcı iş parçacıkları arasında taşıyabilirsiniz.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
