---
title: INotifySink2::OnSyncCallReturn Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
ms.openlocfilehash: ff1dabcfc366607639cd98be4392f8dd59dc83a1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442013"
---
# <a name="inotifysink2onsynccallreturn-method"></a>INotifySink2::OnSyncCallReturn Yöntemi
Bir çağrı geri döndüğünde çağrılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `in_CallID`  
 'ndaki Döndürülen çağrının KIMLIĞI. Bkz. [CALL_ID yapısı](call-id-structure.md).  
  
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
