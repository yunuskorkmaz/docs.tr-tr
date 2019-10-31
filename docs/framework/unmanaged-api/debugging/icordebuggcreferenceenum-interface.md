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
ms.openlocfilehash: 49f89f7d36e74b1fa5921230d7dc6d271d4c0883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134625"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum Arabirimi
Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|Atık olarak toplanabilecek nesneler hakkında bilgi içeren, belirtilen [cor_gc_reference](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) örnek sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugGCReferenceEnum` arabirimi "ıcorhata ayıklama Genum" arabirimini uygular.  
  
 [ICorDebugProcess5:: EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) yöntemini çağırarak bir `ICorDebugGCReferenceEnum` örneği [cor_gc_reference](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) örneklerle doldurulur. [Cor_gc_reference](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) nesneleri [ıcorıtcggcreference:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.  
  
 Bu yöntem tarafından doldurulan koleksiyondaki [cor_gc_reference](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) nesneleri üç tür nesneyi temsil eder:  
  
- Tüm yönetilen yığınlardan nesneler. Bu, Yönetilen koddaki canlı başvuruları ve ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.  
  
- Tanıtıcı tablodaki nesneler. Bu, bir modülde tanımlayıcı başvuruları (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve statik değişkenleri içerir.  
  
- Sonlandırıcı sırasından nesneler. Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
