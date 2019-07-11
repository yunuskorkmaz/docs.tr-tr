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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0c0679dac84089577a2698ed8b0b5497a1a81e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753909"
---
# <a name="corprffunctionargumentrange-structure"></a>COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı
İşlev bağımsız değişkenleri bitişik bellek sırayla soldan sağa depolanan bloğunu temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|`length`|Bitişik blok uzunluğu.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
