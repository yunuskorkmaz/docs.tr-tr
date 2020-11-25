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
ms.openlocfilehash: bb4a8f7ff3ee54474804e3e5620dcce7c9f79fb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726619"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE Yapısı

Atık olarak toplanmış bir nesne hakkındaki bilgileri içerir.  
  
## <a name="syntax"></a>Syntax  
  
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
|`domain`|Tanıtıcının veya nesnenin ait olduğu uygulama etki alanına yönelik bir işaretçi. Değeri olabilir `null` .|  
|`location`|Atık toplanan nesneye karşılık gelen bir ICorDebugValue ya da ICorDebugReferenceValue arabirimi.|  
|`type`|Kökün nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeri. Daha fazla bilgi için, açıklamalar bölümüne bakın.|  
|`extraData`|Atık olarak toplanmış nesne hakkında ek veriler. Bu bilgiler, alanı tarafından belirtildiği gibi nesnenin kaynağına bağlıdır `type` . Daha fazla bilgi için, açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  

 `type`Alan, başvurunun nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeridir. Belirli bir `COR_GC_REFERENCE` değer, aşağıdaki yönetilen nesne türlerinden herhangi birini yansıtabilir:  
  
- Tüm yönetilen yığınlardaki ( `CorGCReferenceType.CorReferenceStack` ) nesneler. Bu, Yönetilen koddaki canlı başvuruların yanı sıra ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.  
  
- Tanıtıcı tablosundan nesneler ( `CorGCReferenceType.CorHandle*` ). Bu, bir modüldeki tanımlayıcı başvuruları ( `HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT` ) ve statik değişkenleri içerir.  
  
- Sonlandırıcı kuyruğundan nesneler ( `CorGCReferenceType.CorReferenceFinalizer` ). Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.  
  
 Bu `extraData` alan, başvurunun kaynağına (veya türüne) bağlı olarak ek veriler içerir. Olası değerler şunlardır:  
  
- `DependentSource`. Eğer ise `type` `CorGCREferenceType.CorHandleStrongDependent` , bu alan, etkin ise, nesne üzerinde çöp toplanabilecek nesneyi köklendirilir `COR_GC_REFERENCE.Location` .  
  
- `RefCount`. İse, `type` `CorGCREferenceType.CorHandleStrongRefCount` Bu alan tanıtıcının başvuru sayısıdır.  
  
- `Size`. `type`İse `CorGCREferenceType.CorHandleStrongSizedByref` , bu alan çöp toplayıcının nesne köklerinin hesaplandığı nesne ağacının son boyutudur. Bu hesaplamanın güncel olduğunu unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
