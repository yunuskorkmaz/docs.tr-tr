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
ms.openlocfilehash: cc5a06e6b3cc1e9338d860cdb110bf7d516080be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404030"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy Sabit Listesi
Bir hata ayıklayıcısı yerel görüntü önbellekten yerel (NGen) görüntüler yükler olup olmadığını belirleyen bir değer sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|İçinde bir [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] uygulama, yerel yerel görüntü önbelleği görüntülerden kullanımını devre dışı bırakıldı. Bir masaüstü uygulamasının bu ayarın etkisi yoktur.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CorDebugNGENPolicy` Numaralandırması tarafından kullanılan [Icordebugprocess5::enablengenpolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) yöntemi. Yerel yerel görüntü önbelleği görüntülerden kullanımını devre dışı bırakma, hata ayıklayıcı en iyi duruma getirilmiş yerel görüntüler yerine debuggable JIT derlenmiş görüntüleri yükler sağlayarak için hata ayıklama tutarlı bir deneyim sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
