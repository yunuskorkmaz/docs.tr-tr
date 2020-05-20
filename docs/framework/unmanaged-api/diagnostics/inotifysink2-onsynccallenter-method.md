---
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
ms.openlocfilehash: 85f00698f42f120b209cca14f293a58ae4c65f6f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442039"
---
# <a name="inotifysink2onsynccallenter-method"></a>INotifySink2::OnSyncCallEnter Yöntemi
Bir çağrı girilirken çağrılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
