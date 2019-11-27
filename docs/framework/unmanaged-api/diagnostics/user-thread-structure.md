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
ms.openlocfilehash: 51db7a2b6464b562e09ce061991898a8d604ead1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437972"
---
# <a name="user_thread-structure"></a>USER_THREAD Yapısı
Bir iş parçacığı hakkındaki hata ayıklayıcıyla ilgili bilgi sağlar. Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`pSidBuffer`|İş parçacığı arabelleğinin adresi.|  
|`dwSidLen`|İş parçacığı arabelleğinin bayt cinsinden uzunluğu.|  
|`dwTid`|İş parçacığı KIMLIĞI.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SetNotifyFilter Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
