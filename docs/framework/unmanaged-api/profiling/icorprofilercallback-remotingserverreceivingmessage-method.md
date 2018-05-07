---
title: ICorProfilerCallback::RemotingServerReceivingMessage Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1874b5bea465eb31bcaad2d912b90d35cfc711b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>ICorProfilerCallback::RemotingServerReceivingMessage Yöntemi
Profil Oluşturucu işlemi bir uzak yöntem çağırma veya etkinleştirme isteği aldı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pCookie`  
 [in] Karşılık gelecek bir değerle sağlanan [Icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) Bu koşullar altında:  
  
-   Remoting GUID tanımlama bilgilerini etkindir.  
  
-   Kanal ileti iletilirken başarılı olur.  
  
-   GUID tanımlama bilgileri için istemci tarafı işlemi üzerinde etkindir.  
  
 Bu, uzak çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.  
  
 `fIsAsync`  
 [in] Bir değer `true` çağrısı, zaman uyumsuz Aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İleti isteği zaman uyumsuz ise, istek rasgele bir iş parçacığı tarafından hizmet verebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
