---
title: ICorDebugStepper Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper
helpviewer_keywords: ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83d394669270eb26b33e084b20a621e18b5b14aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepper-interface1"></a>ICorDebugStepper Interface1
Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Deactivate yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Bu neden `ICorDebugStepper` aldığı son adımı komutunu iptal etmek için.|  
|[Isactive yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Gösteren bir değer alır olup olmadığını bu `ICorDebugStepper` bir adım gerçekleştirmektedir.|  
|[Setınterceptmask yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|İçine adım adım kod türlerini belirten bir Cordebugıntercept değeri ayarlar.|  
|[Setrangeıl yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Gösteren bir değer ayarlar olup olmadığını çağrılar [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) yerel kod göreli veya Microsoft Ara dili (MSIL) koduna üzerinden adım adım yöntemin bağımsız değişken değeri geçirin.|  
|[SetUnmappedStopMask yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|İçinde yürütme durdurulur eşlenmemiş kod türünü belirten bir CorDebugUnmappedStop değeri ayarlar.|  
|[Step yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Bu neden olur `ICorDebugStepper` tek adımlı içeren kendi iş parçacığı aracılığıyla ve isteğe bağlı olarak için için iş parçacığı içinde adlı işlevler üzerinden tek atlama devam edin.|  
|[StepOut yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Bu neden `ICorDebugStepper` tek adımlı içeren kendi iş parçacığı aracılığıyla ve tam olduğunda geçerli çerçeve arama çerçeveye denetimini döndürür.|  
|[StepRange yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Bu neden `ICorDebugStepper` isteğe bağlı olarak tek adımlı için içeren kendi iş parçacığı aracılığıyla ve ne zaman döndürmek için son belirtilen aralıkların dışında kod ulaşır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugStepper` Arabirimi aşağıdaki amaçlara hizmet eder:  
  
-   Verilen bir adım komutu tamamlandığında bu komut, arasındaki bir tanımlayıcı işlevi görür.  
  
-   Gerçekleştirilebilecek tüm atlama kapsülleyen bir merkezi arabirimi sağlar.  
  
-   Erken bir sürüm işlemi iptal etmek için bir yol sağlar.  
  
 İş parçacığı başına birden fazla Adımlayıcı olabilir. Örneğin, bir işlev atlama sırasında bir kesme noktası isabet ve kullanıcı bu işlev içinde yeni bir sürüm işlemini başlatmak isteyebilir. Bu durum nasıl ele alınacağını belirlemek için hata ayıklayıcı kadar olur. Hata ayıklayıcı özgün sürüm işlemi iptal edin veya iki işlem iç içe isteyebilirsiniz. `ICorDebugStepper` Arabirimi her iki seçenek destekler.  
  
 Ortak dil çalışma zamanı (CLR) arası iş parçacıklı, sıralanmış bir çağrı yaparsa Adımlayıcı iş parçacıkları arasında taşıyabilirsiniz.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
