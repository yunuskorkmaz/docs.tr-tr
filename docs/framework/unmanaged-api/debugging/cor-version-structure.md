---
title: COR_VERSION Yapısı
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffbe571ebc3d14c12e57b1f805d77e56e97d12e1
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274182"
---
# <a name="cor_version-structure"></a>COR_VERSION Yapısı
Ortak dil çalışma zamanının Standart Dört parçalı sürüm numarasını depolar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`dwMajor`|Ana sürüm numarası.|  
|`dwMinor`|İkincil sürüm numarası.|  
|`dwBuild`|Yapı numarası.|  
|`dwSubBuild`|Alt yapı numarası.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sürüm numarası 1.0.3705.288 ise, 1 ana sürüm numarasıdır, 0 küçük sürüm numarasıdır, 3705 derleme numarasıdır ve 288 alt yapı numarasıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
