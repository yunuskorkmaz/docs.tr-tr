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
ms.openlocfilehash: 5feda2ce6dc97576d0b1d4f16ca2b9dd5f3fb05e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718570"
---
# <a name="cor_prf_function_argument_info-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı

İşlevin bağımsız değişkenlerini soldan sağa sırada temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
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
|`numRanges`|Bağımsız değişken blok sayısı. Diğer bir deyişle, bu değer dizideki [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapıların sayısıdır `ranges` .|  
|`totalArgumentSize`|Tüm bağımsız değişkenlerin toplam boyutu. Diğer bir deyişle, bu değer bağımsız değişken uzunluklarının toplamıdır.|  
|`ranges`|`COR_PRF_FUNCTION_ARGUMENT_RANGE`Her biri bir işlev bağımsız değişkenlerinin bloğunu temsil eden yapıların dizisi.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir işlevde birçok bağımsız değişken olabilir. Bu bağımsız değişkenler bellekte bitişik olarak depolanmayabilir. Tek bir yerde üç bağımsız değişkeni, başka bir yerde iki bağımsız değişken bloğunu ve bir bağımsız değişkenin son bloğunu farklı bir yerde engellemeniz olabilir. Bu bağımsız değişkenlerin hepsi aynı işleve yöneliktir; yalnızca farklı yerlerde depolanırlar.  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO`Yapı, tek bir işlevin tüm bağımsız değişkenlerini temsil eder. İşlev bağımsız değişkenlerinin tüm bloklarına başvurmak için bir dizi kullanır. Bu nedenle, tek bir işlev için, `COR_PRF_FUNCTION_ARGUMENT_INFO` `COR_PRF_FUNCTION_ARGUMENT_RANGE` her biri bir veya daha fazla işlev bağımsız değişkenine işaret eden birden çok yapıya başvuran tek bir yapıya sahip olursunuz.  
  
 Yazmaçlarda depolanan bağımsız değişkenler, yapıları oluşturmak için belleğe alınır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](profiling-structures.md)
