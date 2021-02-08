---
description: 'Şu konuda daha fazla bilgi edinin: INotifySink2:: OnSyncCallEnter yöntemi'
title: INotifySink2::OnSyncCallEnter Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
ms.openlocfilehash: e7537b16ec8ea8d92ad92498c1bfdac5a9de6475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800285"
---
# <a name="inotifysink2onsynccallenter-method"></a>INotifySink2::OnSyncCallEnter Yöntemi

Bir çağrı girilirken çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `in_CallID`  
 'ndaki Girilen çağrının KIMLIĞI. Bkz. [CALL_ID yapısı](call-id-structure.md).  
  
 `in_pBuffer`  
 'ndaki Çağrı arabelleği.  
  
 `in_BufferSize`  
 'ndaki Çağrı arabelleğinin bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifySink2 Arabirimi](inotifysink2-interface.md)
- [INotifySource2 Arabirimi](inotifysource2-interface.md)
- [INotifyConnection2 Arabirimi](inotifyconnection2-interface.md)
