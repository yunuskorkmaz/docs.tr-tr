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
ms.openlocfilehash: e3aed85e989313e4778e12a6f6bb789ccef49747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423377"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 Arabirimi
Çöp toplama yönetilen nesnelerin hakkında bilgi sağlamak için Yönetilen yığın erişimi desteklemek için Icordebugprocess arabirimi genişletir ve bir hata ayıklayıcı olup olmadığını belirlemek için uygulama yerel yerel görüntü önbellekten görüntüleri yükler.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnableNGenPolicy Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Yönetilen hata ayıklayıcı altında çalışırken yerel görüntüler nasıl bir uygulamanın yüklediği belirleyen bir değer ayarlar.|  
|[EnumerateGCReferences Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Bir işlemde atık olarak toplanmış olacak tüm nesneleri için bir numaralandırıcı alır.|  
|[EnumerateHandles Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Bir numaralandırıcı Nesne tanıtıcıları için bir işlem olarak alır.|  
|[EnumerateHeap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Bir numaralandırıcı nesneler için yönetilen yığında alır.|  
|[EnumerateHeapRegions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Yönetilen yığın bölgeler için bir numaralandırıcı alır.|  
|[GetArrayLayout Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Bellekte bir dizi düzeni hakkındaki bilgileri alır.|  
|[GetGCHeapInformation Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Bir işaretçi alır bir [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) yönetilen yığında atık olarak toplanmış olacak nesneler hakkında bilgi içeren yapısı.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Bir işaretçi yönetilen yığında bir nesneyi alır.|  
|[GetTypeFields Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Kendi türü tanımlayıcısına göre bir türü için alan bilgilerini içeren bir dizi için bir işaretçi alır.|  
|[GetTypeForTypeID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Kendi türü tanımlayıcılarını dayalı bir nesne hakkında bilgi sağlayan bir türü nesnesini alır.|  
|[GetTypeID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Tür tanımlayıcısı nesne için belirtilen bir adres alır.|  
|[GetTypeLayout Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Kendi türü tanımlayıcısına göre bellekte bir nesnenin düzeni hakkındaki bilgileri alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim Icordebugprocess Icordebugprocess2, mantıksal olarak genişletir ve [Icordebugprocess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) arabirimleri.  
  
> [!NOTE]
>  Bu arabirim, başka bir makineden veya başka bir işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
