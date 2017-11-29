---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3571f546f71515a980c5415e568ae85eb0863d42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock Metodu
Bu nesne üzerinde İzleyici kilit sahibi yönetilen iş parçacığı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppThread`  
 [out] Bu nesne üzerinde İzleyici kilit sahibi yönetilen iş parçacığı.  
  
 `pAcquisitionCount`  
 [out] Bu iş parçacığı sahipsiz için döndürmeden önce kilidi zorunda sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|S_FALSE|Yönetilen hiçbir iş parçacığı bu nesnede İzleyici kilit sahibi.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen iş parçacığı bu nesnede İzleyici kilit sahipse:  
  
-   Bu yöntem S_OK döndürür.  
  
-   İş parçacığı çıkar kadar iş parçacığı nesne geçerli değil.  
  
 Yönetilen hiçbir iş parçacığı bu nesne üzerinde İzleyici kilit sahipse `ppThread` ve `pAcquisitionCount` aynıdır, ve S_FALSE yöntemi döndürür.  
  
 Varsa `ppThread` veya `pAcquisitionCount` geçerli bir işaretçi değil sonucu tanımlanmadı.  
  
 Sağlayacak şekilde, iş parçacığı varsa, bu nesne üzerinde İzleyici kilit sahibi belirlenemiyor bir hata oluşursa hata olduğunu gösteren bir HRESULT yöntemi döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
