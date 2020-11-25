---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: 028395b1c8677d07d4a6481740ecdc7ebb48c180
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718533"
---
# <a name="cor_prf_function_argument_range-structure"></a>COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı

Bitişik olarak depolanan bir işlev bağımsız değişkenlerinin bloğunu, bellekte soldan sağa doğru sırada olacak şekilde gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üyeler|Açıklama|  
|-------------|-----------------|  
|`startAddress`|Bloğun başlangıç adresi.|  
|`length`|Bitişik bloğun uzunluğu.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](profiling-structures.md)
