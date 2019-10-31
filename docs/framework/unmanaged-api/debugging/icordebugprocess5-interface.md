---
title: ICorDebugProcess5 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
ms.openlocfilehash: 64fb60abf4f5730dbc15204dbc034b08cacefab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121245"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 Arabirimi
Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel yerel görüntü önbelleğinden görüntü yükleyip yüklememeyeceğini anlamak için ICorDebugProcess arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnableNGenPolicy Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir değer ayarlar.|  
|[EnumerateGCReferences Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Bir işlemde çöp toplanabilecek tüm nesneler için bir Numaralandırıcı alır.|  
|[EnumerateHandles Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|İşlemdeki nesne tanıtıcıları için bir Numaralandırıcı alır.|  
|[EnumerateHeap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Yönetilen yığında nesneler için bir Numaralandırıcı alır.|  
|[EnumerateHeapRegions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Yönetilen yığının bölgeleri için bir Numaralandırıcı alır.|  
|[GetArrayLayout Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Bellekteki bir dizinin yerleşimi hakkında bilgi alır.|  
|[GetGCHeapInformation Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Yönetilen yığında atık olarak toplanabilecek nesneler hakkında bilgi içeren bir [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) yapısına yönelik bir işaretçi alır.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Yönetilen yığında bir nesneye yönelik bir işaretçi alır.|  
|[GetTypeFields Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Tür tanımlayıcısına dayanan bir tür için alan bilgilerini içeren bir diziye yönelik bir işaretçi alır.|  
|[GetTypeForTypeID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Tür tanımlayıcılarına göre bir nesne hakkında bilgi sağlayan bir tür nesnesi alır.|  
|[GetTypeID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Belirtilen adresteki nesnenin tür tanımlayıcısını alır.|  
|[GetTypeLayout Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Bir nesnenin tür tanımlayıcısına göre bellek içindeki düzeni hakkında bilgi alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, ICorDebugProcess, ICorDebugProcess2 ve [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) arabirimlerini mantıksal olarak genişletir.  
  
> [!NOTE]
> Bu arabirim, başka bir makineden ya da başka bir işlemden uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
