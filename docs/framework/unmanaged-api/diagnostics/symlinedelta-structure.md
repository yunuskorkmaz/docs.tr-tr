---
title: SYMLINEDELTA Yapısı
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438006"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA Yapısı
Düzenleme sonucu olarak taşınan yöntemler hakkında sembol işleyicisine bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`mdMethod`|Metodun meta veri belirteci.|  
|`delta`|Yöntemin taşındığı satır sayısı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** Corsya. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
