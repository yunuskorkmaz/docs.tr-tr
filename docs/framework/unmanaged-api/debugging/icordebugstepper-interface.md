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
ms.openlocfilehash: 622fdfa37c93e406950e73941775828ae4b112fa
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379431"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper Arabirimi
Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Deactivate Yöntemi](icordebugstepper-deactivate-method.md)|Bunun `ICorDebugStepper` , aldığı son adım komutunu iptal etmesine neden olur.|  
|[IsActive Yöntemi](icordebugstepper-isactive-method.md)|Bu `ICorDebugStepper` , şu anda bir adım yürütüp yürütümeyeceğini belirten bir değer alır.|  
|[SetInterceptMask Yöntemi](icordebugstepper-setinterceptmask-method.md)|İçine eklenen kod türlerini belirten bir Cordebugkesmenoktası değeri ayarlar.|  
|[SetRangeIL Yöntemi](icordebugstepper-setrangeil-method.md)|[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) öğesine yapılan çağrıların, yerel koda göreli bağımsız değişken değerlerini veya bir şekilde ele alınan metodun Microsoft ara DILI (MSIL) kodunu geçirip geçirmediğini belirten bir değer ayarlar.|  
|[SetUnmappedStopMask Yöntemi](icordebugstepper-setunmappedstopmask-method.md)|Yürütmenin durdurulacağı eşlenmemiş kodun türünü belirten bir CorDebugUnmappedStop değeri ayarlar.|  
|[Step Yöntemi](icordebugstepper-step-method.md)|Bunun, `ICorDebugStepper` kendi iş parçacığı içinde tek adımlı ve isteğe bağlı olarak, iş parçacığı içinde çağrılan işlevler aracılığıyla tek adımla devam etmesine neden olur.|  
|[StepOut Yöntemi](icordebugstepper-stepout-method.md)|Bunun `ICorDebugStepper` , kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve geçerli çerçeve çağıran çerçeveye denetim döndürdüğünde tamamlanmasına neden olur.|  
|[StepRange Yöntemi](icordebugstepper-steprange-method.md)|Bunun `ICorDebugStepper` , kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve belirtilen aralıkların en son ötesinde koda ulaştığında dönüşmesine neden olur.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugStepper`Arabirim aşağıdaki amaçlara hizmet eder:  
  
- Verilen bir step komutu ve bu komutun tamamlanması arasında bir tanımlayıcı görevi görür.  
  
- Gerçekleştirilebilecek tüm adımlamayı kapsüllemek için merkezi bir arabirim sağlar.  
  
- Bir atlama işlemini erken iptal etmek için bir yol sağlar.  
  
 İş parçacığı başına birden fazla Stepper olabilir. Örneğin, bir işlev üzerinde atlama sırasında bir kesme noktası isabet edebilir ve Kullanıcı bu işlevin içinde yeni bir Adımlama işlemi başlatmak isteyebilir. Bu durumun nasıl işleneceğini belirleme, hata ayıklayıcıya yöneliktir. Hata ayıklayıcı orijinal atlama işlemini iptal etmek veya iki işlemi iç içe aktarmak isteyebilir. `ICorDebugStepper`Arabirim her iki seçeneği de destekler.  
  
 Ortak dil çalışma zamanı (CLR), çapraz iş parçacıklı, sıralanmış bir çağrı yapıyorsa, iş parçacıkları arasında Stepper bir geçiş olabilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
