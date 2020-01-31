---
title: CorDebugMDAFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: 34a66a8afa118ecaaaeea0b7b78daaadf1da7509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778269"
---
# <a name="cordebugmdaflags-enumeration"></a>CorDebugMDAFlags Numaralandırması
Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|Mda 'ın tetiklenme iş parçacığı, MDA ' ın tetiklenmesinden sonra kaymış.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı yığını artık MDA ' ın ilk olarak oluşturulduğunu açıkladığında, iş parçacığının *kaymış*olduğu kabul edilir. Bu, iş parçacığının çıkış sırasında geçersiz bir işlemin yürütülmesi ile ilgili olarak ortaya çıkan olağan dışı bir işlemdir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
