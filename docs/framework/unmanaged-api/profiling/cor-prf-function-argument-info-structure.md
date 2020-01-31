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
ms.openlocfilehash: c92ee580caed9f1fb87a31b676747769ad31a0e2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867262"
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
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`numRanges`|Bağımsız değişken blok sayısı. Diğer bir deyişle, bu değer `ranges` dizisindeki [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapılarının sayısıdır.|  
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

- [Profil Oluşturma Yapıları](profiling-structures.md)
