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
ms.openlocfilehash: 2b01acbd617b13a64ef3dca6c8661f1e6bb067ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447387"
---
# <a name="cor_prf_function_argument_info-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı
İşlevin bağımsız değişkenlerini soldan sağa sırada temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`numRanges`|Bağımsız değişken blok sayısı. Diğer bir deyişle, bu değer `ranges` dizisindeki [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) yapılarının sayısıdır.|  
|`totalArgumentSize`|Tüm bağımsız değişkenlerin toplam boyutu. Diğer bir deyişle, bu değer bağımsız değişken uzunluklarının toplamıdır.|  
|`ranges`|Her biri bir işlev bağımsız değişkenlerinin bloğunu temsil eden `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapılarının bir dizisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işlevde birçok bağımsız değişken olabilir. Bu bağımsız değişkenler bellekte bitişik olarak depolanmayabilir. Tek bir yerde üç bağımsız değişkeni, başka bir yerde iki bağımsız değişken bloğunu ve bir bağımsız değişkenin son bloğunu farklı bir yerde engellemeniz olabilir. Bu bağımsız değişkenlerin hepsi aynı işleve yöneliktir; yalnızca farklı yerlerde depolanırlar.  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO` yapısı, tek bir işlevin tüm bağımsız değişkenlerini temsil eder. İşlev bağımsız değişkenlerinin tüm bloklarına başvurmak için bir dizi kullanır. Bu nedenle, tek bir işlev için, her biri bir veya daha fazla işlev bağımsız değişkenine işaret eden birden çok `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapısına başvuran tek bir `COR_PRF_FUNCTION_ARGUMENT_INFO` yapısı vardır.  
  
 Yazmaçlarda depolanan bağımsız değişkenler, yapıları oluşturmak için belleğe alınır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
