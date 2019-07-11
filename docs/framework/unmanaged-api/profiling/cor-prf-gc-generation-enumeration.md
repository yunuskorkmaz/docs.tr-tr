---
title: COR_PRF_GC_GENERATION Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74e70f58600205d44a9ba052981b2cc67b3a44ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753814"
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION Numaralandırması
Bir çöp toplama nesil tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|Nesne, nesil 0 ' depolanır.|  
|`COR_PRF_GC_GEN_1`|Nesne, 1. nesil depolanır.|  
|`COR_PRF_GC_GEN_2`|Nesne, nesil 2'olarak depolanır.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|Nesne büyük nesne yığınında depolanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çöp toplayıcı, üzerinde yaş tabanlı nesiller halinde bölme nesneler tarafından bellek yönetim performansını artırır. Çöp toplayıcı, şu anda üç nesil, 0, 1 ve 2 yanı sıra büyük nesneler için kullanılan özel yığının kesimi numaralı kullanır. Nesneleri belirli bir değere boyutu büyüktür büyük nesne yığınında depolanır. Diğer ayrılmış nesneleri nesil 0 ait kullanıma başlatın. Nesil 0 çöp toplama gerçekleştikten sonra mevcut tüm nesneler, kuşak 1 yükseltilir. Nesil 1 çöp toplama gerçekleştikten sonra mevcut nesneleri 2. nesle taşıyın.  
  
 Nesiller kullanımı, çöp toplayıcı herhangi bir anda yalnızca bir alt kümesi ayrılan nesnelerin ile çalışmak olduğu anlamına gelir.  
  
 `COR_PRF_GC_GENERATION` Numaralandırması tarafından kullanılan [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
