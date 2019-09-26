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
ms.openlocfilehash: cc0b67621f77c0741e0b63b84ab1794530d6280b
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274232"
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
|`extraData`|Atık olarak toplanmış nesne hakkında ek veriler. Bu bilgiler, `type` alanı tarafından belirtildiği gibi nesnenin kaynağına bağlıdır. Daha fazla bilgi için, açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Alan, başvurunun nereden geldiğini gösteren bir CorGCReferenceType numaralandırma değeridir. [](corgcreferencetype-enumeration.md) `type` Belirli `COR_GC_REFERENCE` bir değer, aşağıdaki yönetilen nesne türlerinden herhangi birini yansıtabilir:  
  
- Tüm yönetilen yığınlardaki (`CorGCReferenceType.CorReferenceStack`) nesneler. Bu, Yönetilen koddaki canlı başvuruların yanı sıra ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.  
  
- Tanıtıcı tablosundan nesneler (`CorGCReferenceType.CorHandle*`). Bu, bir modüldeki tanımlayıcı`HNDTYPE_STRONG` başvuruları `HNDTYPE_REFCOUNT`(ve) ve statik değişkenleri içerir.  
  
- Sonlandırıcı kuyruğundan nesneler (`CorGCReferenceType.CorReferenceFinalizer`). Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.  
  
 Bu `extraData` alan, başvurunun kaynağına (veya türüne) bağlı olarak ek veriler içerir. Olası değerler şunlardır:  
  
- `DependentSource`. Eğer ise, bu alan, etkin ise, nesne üzerinde `COR_GC_REFERENCE.Location`çöp toplanabilecek nesneyi köklendirilir. `CorGCREferenceType.CorHandleStrongDependent` `type`  
  
- `RefCount`. `type` İse`CorGCREferenceType.CorHandleStrongRefCount`, bu alan tanıtıcının başvuru sayısıdır.  
  
- `Size`. `type` İse`CorGCREferenceType.CorHandleStrongSizedByref`, bu alan çöp toplayıcının nesne köklerinin hesaplandığı nesne ağacının son boyutudur. Bu hesaplamanın güncel olduğunu unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
