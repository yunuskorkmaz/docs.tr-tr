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
ms.openlocfilehash: 058c66af85da6c902e3d628e1b1479bb88c4fa85
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704857"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a>ICorProfilerCallback::RemotingClientReceivingReply Yöntemi

Profil oluşturucuya, uzaktan iletişim çağrısının sunucu tarafı bölümünün tamamlandığını ve istemcinin artık yanıtı aldığını ve yanıt işlemesini bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a>Parametreler  

 `pCookie`  
 'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) içinde belirtilen değere karşılık gelen bir değer:  
  
- Uzaktan iletişim GUID tanımlama bilgileri etkin.  
  
- Kanal, iletiyi iletmede başarılı olur.  
  
- GUID tanımlama bilgileri, sunucu tarafı işleminde etkindir.  
  
 Bu, uzaktan iletişim çağrılarının kolayca eşleştirilmesini sağlar.  
  
 `fIsAsync`  
 'ndaki `true` Çağrının zaman uyumsuz olduğu bir değer; Aksi takdirde, `false` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
