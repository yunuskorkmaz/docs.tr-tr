---
title: ICorProfilerCallback::RemotingClientReceivingReply Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: f7a943627e2087e6b8c78ced9fc32824843d44fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175141"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a>ICorProfilerCallback::RemotingClientReceivingReply Yöntemi
Profiloluşturucuya, remoting çağrısının sunucu tarafındaki bölümünün tamamlandığını ve istemcinin şimdi yanıtı aldığını ve işlemek üzere olduğunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a>Parametreler  
 `pCookie`  
 [içinde] Bu koşullar altında ICorProfilerCallback sağlanan değer ile karşılık gelecek bir [değer::RemotingServerSendingReply:](icorprofilercallback-remotingserversendingreply-method.md)  
  
- GUID tanımlama bilgilerini remoting etkindir.  
  
- Kanal iletiyi iletmede başarılı dır.  
  
- GUID tanımlama bilgileri sunucu tarafında etkindir.  
  
 Bu, remoting çağrılarının kolay eşleşmesini sağlar.  
  
 `fIsAsync`  
 [içinde] Arama nın `true` eşzamanlı olması durumunda ki değer; aksi `false`takdirde, .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
