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
ms.openlocfilehash: 0178e2a7877803644bb25e6700306d7ac2ef2d4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215904"
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION Numaralandırması
Bir çöp toplama nesil tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
