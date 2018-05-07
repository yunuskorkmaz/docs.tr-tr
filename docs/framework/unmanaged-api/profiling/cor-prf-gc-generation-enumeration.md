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
ms.openlocfilehash: 8283139566050b1858a003316dc46581822a9bbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION Numaralandırması
Çöp toplama nesil tanımlar.  
  
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
|`COR_PRF_GC_GEN_0`|Nesne oluşturma 0 depolanır.|  
|`COR_PRF_GC_GEN_1`|Nesne, 1. nesil depolanır.|  
|`COR_PRF_GC_GEN_2`|Nesne, 2. nesil depolanır.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|Nesne büyük nesne yığın depolanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çöp toplayıcı üzerinde yaş tabanlı nesli içine bölme nesneler tarafından bellek yönetimi performansı artırır. Çöp toplayıcı şu anda üç nesil, 0, 1 ve 2 yanı sıra büyük nesneler için kullanılan özel yığın kesimi numaralı kullanır. Büyüklüğü belirli bir değerden büyük nesneler büyük nesne yığın depolanır. Diğer ayrılmış nesneleri oluşturma 0 ait çıkışı başlatın. Çöp toplama kuşak 0 gerçekleştikten sonra mevcut tüm nesneleri 1. nesil için öne çıkar. Çöp toplama nesil 1 gerçekleştikten sonra mevcut nesneleri 2. nesil taşıyın.  
  
 Nesli kullanımını, atık toplayıcı herhangi bir anda yalnızca bir alt kümesini ayrılmış nesneleri ile çalışmak sahip olduğu anlamına gelir.  
  
 `COR_PRF_GC_GENERATION` Numaralandırması tarafından kullanılan [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
