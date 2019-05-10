---
title: ICorProfilerCallback::RemotingServerSendingReply Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cde75f1f33df83131212b0f7d4b349b20338f3dd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662866"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a>ICorProfilerCallback::RemotingServerSendingReply Yöntemi
Profil Oluşturucu işlemi bir uzak yöntem çağırma isteği işlemeyi tamamladıktan ve yanıt bir kanal üzerinden iletilmek üzere olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pCookie`  
 [in] Sağlanan değerle karşılık gelecek bir GUID işaretçisi [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) Bu koşullar altında:  
  
- Uzaktan iletişim GUID tanımlama bilgilerinin etkin olur.  
  
- Kanal ileti iletilirken başarılı olur.  
  
- GUID tanımlama bilgileri istemci tarafı işlemini üzerinde etkindir.  
  
 Bu, uzak hizmet çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.  
  
 `fIsAsync`  
 [in] Bir değer `true` çağrısı ise, zaman uyumsuz; Aksi takdirde `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
