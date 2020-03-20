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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179326"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE Yapısı
Çöp toplanacak bir nesne hakkında bilgi içerir.  
  
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
|`domain`|Tanıtıcının veya nesnenin ait olduğu uygulama etki alanına işaretçi. Değeri. `null`|  
|`location`|Çöp toplanacak nesneye karşılık gelen bir ICorDebugValue veya ICorDebugReferenceValue arabirimi.|  
|`type`|Kökün nereden geldiğini gösteren [bir CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeri. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`extraData`|Çöp toplanacak nesne yle ilgili ek veriler. Bu bilgiler, alan tarafından belirtildiği gibi nesnenin `type` kaynağına bağlıdır. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Alan, `type` başvurunun nereden geldiğini gösteren bir [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırma değeridir. Belirli `COR_GC_REFERENCE` bir değer, aşağıdaki yönetilen nesnelerden herhangi birini yansıtabilir:  
  
- Yönetilen tüm yığınlardan nesneler`CorGCReferenceType.CorReferenceStack`( ). Bu, yönetilen koddaki canlı başvuruların yanı sıra ortak dil çalışma zamanı tarafından oluşturulan nesneleri de içerir.  
  
- Tutamaç tablosundaki nesneler`CorGCReferenceType.CorHandle*`( ). Bu, bir`HNDTYPE_STRONG` modüldeki güçlü başvuruları ( ve ) ve `HNDTYPE_REFCOUNT`statik değişkenleri içerir.  
  
- Sonlandırıcı sıradaki nesneler (`CorGCReferenceType.CorReferenceFinalizer`). Sonlandırıcı sıra, sonlandırıcı çalışana kadar nesneleri kökler.  
  
 Alan, `extraData` başvurunun kaynağına (veya türüne) bağlı olarak ek veri içerir. Olası değerler şunlardır:  
  
- `DependentSource`. `type` Ise `CorGCREferenceType.CorHandleStrongDependent`, bu alan nesne ise, eğer canlı, kökler nesne çöp `COR_GC_REFERENCE.Location`toplanan.  
  
- `RefCount`. `type` Ise `CorGCREferenceType.CorHandleStrongRefCount`, bu alan tanıtıcının başvuru sayısıdır.  
  
- `Size`. `type` Ise `CorGCREferenceType.CorHandleStrongSizedByref`, bu alan, çöp toplayıcınesne kökleri hesaplanan nesne ağacının son boyutudur. Bu hesaplamanın güncel olmaması gerektiğini unutmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata ayıklama](index.md)
