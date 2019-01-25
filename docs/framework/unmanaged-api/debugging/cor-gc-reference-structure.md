---
title: COR_GC_REFERENCE Yapısı
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0375fdd6f86ae89171545cfdcb44ac37074084e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718721"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE Yapısı
Atık olarak toplanmış olacak bir nesneyle ilgili bilgileri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`domain`|Bir işaretçi tanıtıcı veya nesne ait olduğu uygulama etki alanı. Değeri aşağıdakilerden biri olabilir `null`.|  
|`location`|Bir Icordebugvalue veya atık olarak toplanmış olmasını nesnesine karşılık gelen bir Icordebugreferencevalue arabirimi.|  
|`type`|A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) kök nereden geldiğini belirten numaralandırma değeri. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`extraData`|Atık olarak toplanmış alınacak nesneyi ilgili ek veriler. Bu bilgileri gösterildiği gibi kaynak nesnenin bağlıdır `type` alan. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `type` Alan bir [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) başvuru nereden geldiğini belirten numaralandırma değeri. Belirli bir `COR_GC_REFERENCE` değerini herhangi bir yönetilen nesneler aşağıdaki türde yansıtmak:  
  
-   Tüm yönetilen yığında nesneleri (`CorGCReferenceType.CorReferenceStack`). Bu, ortak dil çalışma zamanı tarafından oluşturulan nesnelerin yanı sıra yönetilen kod kullanarak canlı başvurular içerir.  
  
-   Nesne işleyicisi tablosundan (`CorGCReferenceType.CorHandle*`). Bu güçlü atıflar içerir (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve Modül içindeki statik değişkenler.  
  
-   Sonlandırma sırasından nesneleri (`CorGCReferenceType.CorReferenceFinalizer`). Sonlandırıcı çalıştırılana dek Sonlandırıcı kuyruğunda nesneleri kökleri.  
  
 `extraData` Alanı başvuru kaynağı (veya tür) bağlı olarak ek veri içeriyor. Olası değerler şunlardır:  
  
-   `DependentSource`. Varsa `type` olduğu `CorGCREferenceType.CorHandleStrongDependent`, bu alan, etkin değilse, atık olarak toplanmış alınacak nesneyi kökleri nesnedir `COR_GC_REFERENCE.Location`.  
  
-   `RefCount`. Varsa `type` olduğu `CorGCREferenceType.CorHandleStrongRefCount`, tanıtıcı başvurusu sayısı bu alandır.  
  
-   `Size`. Varsa `type` olduğu `CorGCREferenceType.CorHandleStrongSizedByref`, bu alan atık toplayıcı nesne kökleri hesaplanan nesne ağacının son boyutudur. Bu hesaplama mutlaka güncel olmadığını unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
