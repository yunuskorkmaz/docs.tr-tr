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
ms.openlocfilehash: 732bc9d38ca0d6c2dc3f30603a722b7370034b80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408196"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE Yapısı
Çöp toplanan olması için bir nesne hakkında bilgiler içerir.  
  
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
|`domain`|Tanıtıcı veya nesne ait olduğu uygulama etki alanı için bir işaretçi. Değeri aşağıdakilerden biri olabilir `null`.|  
|`location`|Bir Icordebugvalue veya çöpünün toplanma olmasını nesnesine karşılık gelen bir Icordebugreferencevalue arabirimi.|  
|`type`|A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) kök nereden geldiğini belirten numaralandırma değeri. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`extraData`|Çöp toplanan olmasını nesne hakkında ek veriler. Bu bilgiler belirtildiği gibi nesnenin kaynağa bağlıdır `type` alan. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `type` Alan bir [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) başvuru nereden geldiğini belirten numaralandırma değeri. Belirli bir `COR_GC_REFERENCE` değeri herhangi bir yönetilen nesneler şu tür yansıtır:  
  
-   Tüm yönetilen yığınları nesnelerden (`CorGCReferenceType.CorReferenceStack`). Bu Canlı başvuruları ortak dil çalışma zamanı tarafından oluşturulan nesnelerin yanı sıra, yönetilen kod içerir.  
  
-   Tanıtıcı tablosunu nesnelerden (`CorGCReferenceType.CorHandle*`). Bu güçlü başvurular içerir (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve bir modüldeki statik değişkenler.  
  
-   Sonlandırıcı sıranın nesnelerden (`CorGCReferenceType.CorReferenceFinalizer`). Sonlandırıcıyı çalıştırılana dek sonlandırıcıyı sıranın nesneleri kökleri.  
  
 `extraData` Alan başvuru kaynağı (veya türünü) bağlı olarak fazladan verileri içerir. Olası değerler şunlardır:  
  
-   `DependentSource`. Varsa `type` olan `CorGCREferenceType.CorHandleStrongDependent`, bu alan, etkin değilse, atık olarak toplanmış olmasını nesne kökleri nesnedir `COR_GC_REFERENCE.Location`.  
  
-   `RefCount`. Varsa `type` olan `CorGCREferenceType.CorHandleStrongRefCount`, bu alan başvuru tanıtıcısı sayısıdır.  
  
-   `Size`. Varsa `type` olan `CorGCREferenceType.CorHandleStrongSizedByref`, bu alan son atık toplayıcı nesnesi kökleri hesaplanan nesne ağacına boyutudur. Bu hesaplama mutlaka güncel olmadığını unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
