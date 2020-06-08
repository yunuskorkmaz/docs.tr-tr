---
title: COR_PRF_CLAUSE_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: a308017dc80dd973cbf108ba9df824193775f5ff
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501059"
---
# <a name="cor_prf_clause_type-enumeration"></a>COR_PRF_CLAUSE_TYPE Numaralandırması
Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|Exception yan tümcesi geçerli değil.|  
|`COR_PRF_CLAUSE_FILTER`|Exception yan tümcesi bir filtre ifadesidir.|  
|`COR_PRF_CLAUSE_CATCH`|Exception yan tümcesi bir `catch` ifadedir.|  
|`COR_PRF_CLAUSE_FINALLY`|Exception yan tümcesi bir `finally` ifadedir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)
