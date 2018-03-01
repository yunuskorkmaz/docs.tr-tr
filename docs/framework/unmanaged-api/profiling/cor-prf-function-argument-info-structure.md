---
title: "COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e26377fe3c5cfbae68f90087e3fb624ae4db0dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı
Soldan sağa sırayla bir işlevin bağımsız değişkenler temsil eder.  
  
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
|`numRanges`|Bağımsız değişkenler blok sayısı. Diğer bir deyişle, bu değer sayısıdır [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) içindeki yapıları `ranges` dizi.|  
|`totalArgumentSize`|Tüm bağımsız değişkenler toplam boyutu. Diğer bir deyişle, bu değer bağımsız değişken uzunlukta toplamıdır.|  
|`ranges`|Bir dizi `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapıları, her biri bir işlev bağımsız değişkenleri bloğunu temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işlev fazla sayıda bağımsız değişken olabilir. Bu bağımsız değişkenlerden bitişik bellek depolanabilir değil. Tek bir yerde üç bağımsız değişken bloğunu, başka bir yerde iki bağımsız değişken bir blok ve farklı bir yerde tek bir bağımsız değişken son bloğunu olabilir. Bu bağımsız değişkenler tüm aynı işlevin; yalnızca farklı yerlerde depolandıkları.  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO` Yapısı tek bir işlevin tüm bağımsız değişkenler temsil eder. İşlev bağımsız değişkenleri tüm bloklarını başvurmak için bir dizi kullanır. Bu nedenle, tek bir işlev için tek bir elinizde `COR_PRF_FUNCTION_ARGUMENT_INFO` birden çok başvuran yapısı `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapıları, her biri bir veya daha fazla işlev bağımsız değişkenleri için işaret eder.  
  
 Yazmaçları depolanan bağımsız değişkenleri yapılarının belleğe geçmiş.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
