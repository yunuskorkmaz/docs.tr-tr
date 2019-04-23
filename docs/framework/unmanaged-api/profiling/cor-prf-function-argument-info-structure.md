---
title: COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293ad30ebf47ca8684d158b1ae1772ab245d7981
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163123"
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı
Soldan sağa doğru sırayla bir işlevin bağımsız değişkenlerini temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`numRanges`|Bağımsız değişkenlerin blokların sayısı. Diğer bir deyişle, bu değer sayısıdır [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) içindeki yapıları `ranges` dizisi.|  
|`totalArgumentSize`|Tüm bağımsız değişkenler toplam boyutu. Diğer bir deyişle, bu bağımsız değişken uzunluklarının toplamını değerdir.|  
|`ranges`|Bir dizi `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapıları, her biri bir işlev bağımsız değişkenleri bloğunu temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işlev, fazla sayıda bağımsız değişken olabilir. Bu bağımsız değişkenlerden bitişik bellekte depolanması. Tek bir yerde üç bağımsız değişken bir blok, iki bağımsız değişkeni başka bir yerde bloğunu ve farklı bir yerde bir bağımsız değişkenin bir son blok olabilir. Bu bağımsız değişkenler tüm; aynı işlevi farklı yerlerde yalnızca depolandıkları.  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO` Yapısı tek bir işlevin tüm bağımsız değişkenleri temsil eder. Bir dizi işlev bağımsız değişkenlerinin tüm blokları başvurmak için kullanır. Bu nedenle, tek bir sahip tek bir işlev için `COR_PRF_FUNCTION_ARGUMENT_INFO` birden çok başvuran yapısı `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapıları, her biri bir veya daha fazla işlev bağımsız değişkenleri için işaret eder.  
  
 Kayıtlara depolanan bağımsız değişkenler, yapıları yapı belleğe geçmiş.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
