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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948687"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 Arabirimi
Icordebugprocess arabirimi, yönetilen nesnelerin Çöp toplaması hakkında bilgi sağlamak için yönetilen yığına erişimi desteklemek için genişletir ve bir hata ayıklayıcı olup olmadığını belirlemek için uygulama yerel görüntü önbelleğinden görüntüleri yükler.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnableNGenPolicy Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Nasıl bir uygulama yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri yükler belirleyen değeri ayarlar.|  
|[EnumerateGCReferences Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Bir işlemde atık olarak toplanmış olacak olan tüm nesneler için bir numaralandırıcı alır.|  
|[EnumerateHandles Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Numaralandırıcı nesnesi tanıtıcıları için bir işlem olarak alır.|  
|[EnumerateHeap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Bir numaralandırıcı, yönetilen yığındaki nesneler için alır.|  
|[EnumerateHeapRegions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Yönetilen yığının bölgeler için bir numaralandırıcı alır.|  
|[GetArrayLayout Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Bellekte bir dizinin düzeni hakkındaki bilgileri alır.|  
|[GetGCHeapInformation Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Bir işaretçi alır bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) yönetilen yığında atık olarak toplanmış olacak nesneler hakkında bilgi içeren yapısı.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Bir işaretçi, yönetilen yığındaki bir nesneyi alır.|  
|[GetTypeFields Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Kendi tür tanımlayıcısına göre bir türü için alan bilgileri içeren bir dizi için bir işaretçi alır.|  
|[GetTypeForTypeID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Kendi tür tanımlayıcıları hakkında temel bir nesne hakkında bilgi sağlayan bir tür nesnesi alır.|  
|[GetTypeID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Tür tanımlayıcı nesne için belirli bir adreste alır.|  
|[GetTypeLayout Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Kendi tür tanımlayıcısına göre bellekte bir nesne düzeni bilgilerini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim Icordebugprocess Icordebugprocess2, mantıksal olarak genişletir ve [Icordebugprocess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) arabirimleri.  
  
> [!NOTE]
>  Bu arabirim, başka bir makineden ya da başka bir işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
