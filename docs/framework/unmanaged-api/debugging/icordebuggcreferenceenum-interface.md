---
title: ICorDebugGCReferenceEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa8c3160dc779b2475dec63be896af5283cf5346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum Arabirimi
Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|Belirtilen sayıda alır [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çöpünün toplanma olacak nesneleri hakkında bilgi içeren örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugGCReferenceEnum` Arabirimini uygulayan "ICorDebugEnum" arabirimi.  
  
 Bir `ICorDebugGCReferenceEnum` örneği ile doldurulur [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) yöntemi. [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) nesneleri numaralandırılan çağırarak [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) yöntemi.  
  
 [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) bu yöntem tarafından doldurulmuş koleksiyonundaki nesneleri temsil eden nesneler üç tür:  
  
-   Tüm yönetilen yığınları nesneleri. Bu ortak dil çalışma zamanı tarafından oluşturulan nesnelerin yanı sıra, yönetilen kod Canlı başvurular içerir.  
  
-   Tanıtıcı tablosunu nesneleri. Bu güçlü başvurular içerir (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve bir modüldeki statik değişkenler.  
  
-   Nesneleri sonlandırıcıyı sırasından. Sonlandırıcıyı çalıştırılana dek sonlandırıcıyı sıranın nesneleri kökleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
