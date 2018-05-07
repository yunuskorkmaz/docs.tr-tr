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
ms.openlocfilehash: f489ab29726292f6c55151169ad9efc6f0fbfbcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState Numaralandırması
Bir iş parçacığı kullanıcı durumunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`USER_STOP_REQUESTED`|İş parçacığı sonlandırma istendi.|  
|`USER_SUSPEND_REQUESTED`|İş parçacığı ertelenmesi istendi.|  
|`USER_BACKGROUND`|İş parçacığı arka planda çalışıyor.|  
|`USER_UNSTARTED`|Yürütme iş parçacığı başlatılmadı.|  
|`USER_STOPPED`|İş parçacığı sonlandırıldı.|  
|`USER_WAIT_SLEEP_JOIN`|İş parçacığı bir görevi tamamlamak başka bir iş parçacığı için bekliyor.|  
|`USER_SUSPENDED`|İş parçacığı askıya alındı.|  
|`USER_UNSAFE_POINT`|İş parçacığı güvenli olmayan bir noktada ' dir. Diğer bir deyişle, yürütme içindeki bir noktada burada atık toplama engelleyebilir iş parçacığıdır.<br /><br /> Hata ayıklama olayları güvensiz noktalarından gönderilir, ancak bir iş parçacığı güvenli olmayan bir noktada askıya büyük olasılıkla neden olacak bir kilitlenme iş parçacığı sürdürülene kadar. Güvenli ve güvenli olmayan puanları tam zamanında (JIT) ve atık toplama uygulaması tarafından belirlenir.|  
|`USER_THREADPOOL`|İş parçacığı iş parçacığı havuzundan değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir iş parçacığı kullanıcı durumu iş parçacığı hata ayıklayıcı incelerken olan durumdur. Bir iş parçacığı, kullanıcı durumlarını birleşimi olabilir.  
  
 Kullanım [Icordebugthread::getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) bir iş parçacığının kullanıcı durumunu alma yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
