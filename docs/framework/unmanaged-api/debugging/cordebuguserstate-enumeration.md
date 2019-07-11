---
title: CorDebugUserState Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76fbbb3f924f610b604586dca78cab344217b544
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739456"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState Numaralandırması
Kullanıcı durumunu bir iş parçacığının gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>Üyeler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|İş parçacığının sonlandırılması istendi.|  
|`USER_SUSPEND_REQUESTED`|İş parçacığının bir askıya alma isteğinde bulundu.|  
|`USER_BACKGROUND`|İş parçacığı arka planda çalışıyor.|  
|`USER_UNSTARTED`|Yürütme iş parçacığı başlatılmadı.|  
|`USER_STOPPED`|İş parçacığı sonlandırıldı.|  
|`USER_WAIT_SLEEP_JOIN`|İş parçacığı bir görevi tamamlamak başka bir iş parçacığı için bekliyor.|  
|`USER_SUSPENDED`|İş parçacığını askıya alındı.|  
|`USER_UNSAFE_POINT`|İş parçacığı güvenli olmayan bir noktada ' dir. Diğer bir deyişle, yürütme noktasında bir çöp toplama burada engelleyebilir iş parçacığıdır.<br /><br /> Hata ayıklama olaylarını güvenli olmayan noktalarından gönderilir, ancak güvenli olmayan bir noktada bir iş parçacığını askıya büyük olasılıkla neden olacak bir kilitlenme iş parçacığı sürdürülene kadar. Güvenli ve güvenli olmayan noktaları, just-in-time (JIT) ve çöp toplama uygulama tarafından belirlenir.|  
|`USER_THREADPOOL`|İş parçacığı havuzu iş parçacığıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıcı durumunu bir iş parçacığının iş parçacığı hata ayıklayıcısı incelerken olan durumudur. Bir iş parçacığı, kullanıcı durumlarını bir birleşimi olabilir.  
  
 Kullanım [Icordebugthread::getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) bir iş parçacığının kullanıcı durumunu almak için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
