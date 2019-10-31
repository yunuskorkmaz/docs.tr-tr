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
ms.openlocfilehash: 635cb0c003889beb2f78e8413189cbfc4b064175
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099136"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE Yapısı
Atık olarak toplanmış bir nesne hakkındaki bilgileri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`domain`|Tanıtıcının veya nesnenin ait olduğu uygulama etki alanına yönelik bir işaretçi. Değeri `null`olabilir.|  
|`location`|Atık toplanan nesneye karşılık gelen bir ICorDebugValue ya da ICorDebugReferenceValue arabirimi.|  
|`type`|Kökün nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeri. Daha fazla bilgi için, açıklamalar bölümüne bakın.|  
|`extraData`|Atık olarak toplanmış nesne hakkında ek veriler. Bu bilgiler, `type` alanı tarafından belirtilen şekilde nesnenin kaynağına bağlıdır. Daha fazla bilgi için, açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `type` alanı, başvurunun nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeridir. Belirli bir `COR_GC_REFERENCE` değeri aşağıdaki yönetilen nesne türlerinden herhangi birini yansıtabilir:  
  
- Tüm yönetilen yığınlardan nesneler (`CorGCReferenceType.CorReferenceStack`). Bu, Yönetilen koddaki canlı başvuruların yanı sıra ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.  
  
- Tanıtıcı tablosundan nesneler (`CorGCReferenceType.CorHandle*`). Bu, bir modülde tanımlayıcı başvuruları (`HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT`) ve statik değişkenleri içerir.  
  
- Sonlandırıcı kuyruğundan nesneler (`CorGCReferenceType.CorReferenceFinalizer`). Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.  
  
 `extraData` alan, başvurunun kaynağına (veya türüne) bağlı olarak ek veriler içerir. Olası değerler şunlardır:  
  
- `DependentSource`. `type` `CorGCREferenceType.CorHandleStrongDependent`ise, bu alan, etkin olduğunda, nesneyi `COR_GC_REFERENCE.Location`atık olarak toplanabilecek şekilde Kökbir nesnedir.  
  
- `RefCount`. `type` `CorGCREferenceType.CorHandleStrongRefCount`ise, bu alan tanıtıcının başvuru sayısıdır.  
  
- `Size`. `type` `CorGCREferenceType.CorHandleStrongSizedByref`ise, bu alan çöp toplayıcının nesne köklerinin hesaplandığı nesne ağacının son boyutudur. Bu hesaplamanın güncel olduğunu unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
