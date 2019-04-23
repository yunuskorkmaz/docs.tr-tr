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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fabc8f77b12865d0d971b5934d7de27b52f3e813
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159490"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA Yapısı
Sembol işleyici sonucunda düzenlemeleri taşınan yöntemleri hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`mdMethod`|Yöntemin meta veri belirteci.|  
|`delta`|Yöntem taşındı satırların sayısı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
