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
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609306"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA Yapısı
Düzenleme sonucu olarak taşınan yöntemler hakkında sembol işleyicisine bilgi sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`mdMethod`|Metodun meta veri belirteci.|  
|`delta`|Yöntemin taşındığı satır sayısı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** Corsya. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Yapıları](diagnostics-symbol-store-structures.md)
