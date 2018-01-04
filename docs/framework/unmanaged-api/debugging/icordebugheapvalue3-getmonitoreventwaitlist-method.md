---
title: ICorDebugHeapValue3::GetMonitorEventWaitList Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList Metodu
İzleyici kilit ile ilişkili olay sıraya alınan iş parçacıkları sıralı bir listesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppThreadEnum`  
 [out] İş parçacıkları sıralı listesini sağlar Icordebugthreadenum Numaralandırıcı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Liste boş değil.|  
|S_FALSE|Liste boş olduğu.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 Listedeki ilk iş parçacığı için sonraki çağrı tarafından yayınlanan ilk parçacığıdır <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. Sonraki iş parçacığı listesinde aşağıdaki çağrıyı ve benzeri yayımlanır.  
  
 Liste boş değilse, bu yöntem S_OK döndürür. Liste boş ise, yöntem S_FALSE döndürür; Bu durumda, boş olmasına rağmen numaralandırma hala geçerli değil.  
  
 Her iki durumda da, yalnızca geçerli eşitlenmiş durumuna süresince numaralandırması arabirimi kullanılabilir. Ancak, iş parçacığı çıkar kadar ondan dispensed iş parçacığının arabirimleri geçerli değildir.  
  
 Varsa `ppThreadEnum` geçerli bir işaretçi değil sonucu tanımlanmadı.  
  
 Sağlayacak şekilde, varsa, iş parçacıkları izleme için bekleyen belirlenemiyor bir hata oluşursa hata olduğunu gösteren bir HRESULT yöntemi döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
