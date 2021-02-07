---
description: 'Daha fazla bilgi edinin: CodeChunkInfo yapısı'
title: CodeChunkInfo Yapısı
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: 017a9ee8c608d4efae98eb0a342a3371ef8ec310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712356"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo Yapısı

Bellekte tek bir kod öbeğini temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`startAddr`|`CORDB_ADDRESS`Öbekin başlangıç adresini belirten bir değer.|  
|`length`|Öbekin bayt cinsinden boyutu.|  
  
## <a name="remarks"></a>Açıklamalar  

 Tek kod öbeği, bir işlev gibi bir kod nesnesinin parçası olan yerel kod bölgesidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeChunks Yöntemi](icordebugcode2-getcodechunks-method.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
