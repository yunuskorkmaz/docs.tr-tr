---
description: 'Şu konuda daha fazla bilgi edinin: INotifySink2:: OnSyncCallExit Yöntemi'
title: INotifySink2::OnSyncCallExit Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 2de55c3b7956576049e4ad65b2cb6fbc69fa84af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800272"
---
# <a name="inotifysink2onsynccallexit-method"></a>INotifySink2::OnSyncCallExit Yöntemi

Bir çağrıdan çıkarken çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `in_CallID`  
 'ndaki Çıkılmakta olan çağrının KIMLIĞI. Bkz. [CALL_ID yapısı](call-id-structure.md).  
  
 `out_ppBuffer`  
 dışı Çağrı arabelleği.  
  
 `out_pBufferSize`  
 dışı Çağrı arabelleğinin bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifySink2 Arabirimi](inotifysink2-interface.md)
- [INotifySource2 Arabirimi](inotifysource2-interface.md)
- [INotifyConnection2 Arabirimi](inotifyconnection2-interface.md)
