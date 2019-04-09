---
title: CorDebugNGenPolicy Sabit Listesi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca922d8b582c0608073d4fd0ba986167ae470e34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109674"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy Sabit Listesi
Bir hata ayıklayıcı yerel görüntü önbelleğinden kaldırırız (NGen) yerel görüntüleri yükleyip yüklemediğini belirleyen bir değer sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|İçinde bir [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] uygulama, görüntüleri yerel görüntü önbelleğinden kullanımını devre dışı bırakıldı. İçinde bir masaüstü uygulaması, bu ayar etkisizdir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CorDebugNGENPolicy` Numaralandırması tarafından kullanılan [Icordebugprocess5::enablengenpolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) yöntemi. Görüntüleri yerel görüntü önbelleğinden kullanımını devre dışı bırakma, hata ayıklayıcı hata ayıklanabilir JIT olarak derlenmiş görüntüleri yerine en iyi duruma getirilmiş yerel görüntüleri yükler sağlayarak için tutarlı bir hata ayıklama deneyimi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
