---
title: USER_THREAD Yapısı
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609449"
---
# <a name="user_thread-structure"></a>USER_THREAD Yapısı
Bir iş parçacığı hakkındaki hata ayıklayıcıyla ilgili bilgi sağlar. Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) yöntemi.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`pSidBuffer`|İş parçacığı arabelleğinin adresi.|  
|`dwSidLen`|İş parçacığı arabelleğinin bayt cinsinden uzunluğu.|  
|`dwTid`|İş parçacığı KIMLIĞI.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SetNotifyFilter Yöntemi](inotifysource2-setnotifyfilter-method.md)
- [Tanılama Sembol Deposu Yapıları](diagnostics-symbol-store-structures.md)
