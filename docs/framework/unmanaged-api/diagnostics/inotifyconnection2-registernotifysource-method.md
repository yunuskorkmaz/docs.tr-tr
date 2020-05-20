---
title: INotifyConnection2::RegisterNotifySource Yöntemi
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: b7fa777466e2c7edd7b3110dd91e776785c63c58
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442078"
---
# <a name="inotifyconnection2registernotifysource-method"></a>INotifyConnection2::RegisterNotifySource Yöntemi
Belirtilen bir bildirim kaynağını yükleme.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `in_pNotifySource`  
 'ndaki Bildirim kaynağı olarak kullanılacak nesneyi belirtir.  
  
 `out_ppNotifySink`  
 dışı Bildirim havuzu olarak kullanılacak nesneyi alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifyConnection2 Arabirimi](inotifyconnection2-interface.md)
- [INotifySource2 Arabirimi](inotifysource2-interface.md)
- [INotifySink2 Arabirimi](inotifysink2-interface.md)
- [UnregisterNotifySource Yöntemi](inotifyconnection2-unregisternotifysource-method.md)
