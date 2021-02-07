---
description: 'Daha fazla bilgi edinin: SYMLıNEDELTA yapısı'
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
ms.openlocfilehash: ae00d2be9809b48180d2cd99d05e410624033419
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761453"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA Yapısı

Düzenleme sonucu olarak taşınan yöntemler hakkında sembol işleyicisine bilgi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`mdMethod`|Metodun meta veri belirteci.|  
|`delta`|Yöntemin taşındığı satır sayısı.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** Corsya. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Yapıları](diagnostics-symbol-store-structures.md)
