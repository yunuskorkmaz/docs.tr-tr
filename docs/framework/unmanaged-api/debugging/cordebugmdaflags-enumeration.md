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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 732523935eec62bffbc15705bc93c97f14c90064
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148427"
---
# <a name="cordebugmdaflags-enumeration"></a>CorDebugMDAFlags Numaralandırması
Yönetilen hata ayıklama Yardımcısı (MDA) harekete geçirilen iş parçacığı durumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|MDA harekete geçirildi beri MDA harekete geçirildi iş parçacığı kaymış.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı yığınını artık burada MDA başlangıçta tetiklendi açıkladığında, iş parçacığının sahip olduğu kabul edildiği *kaymış*. Bu, iş parçacığının yürütülmesini çıkarken geçersiz bir işlem tarafından hazırlanmıştır olağan dışı bir durumdur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
