---
title: "ICLRTask2::BeginPreventAsyncAbort Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2.BeginPreventAsyncAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33136dfbfa8bb3e0147bc1a1c1bb9e88ab2e4239
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask2beginpreventasyncabort-method"></a>ICLRTask2::BeginPreventAsyncAbort Yöntemi
Geçerli iş parçacığında iş parçacığı iptalleri sonuçlanmasını gecikmeler yeni iş parçacığı iptal istekleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HOST_E_INVALIDOPERATION|Yöntemi, geçerli iş parçacığının olmayan bir iş parçacığında çağrıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemin çağrılması geçerli iş parçacığının gecikme iş parçacığı iptal sayaç bire artırır.  
  
 Çağrılar `BeginPreventAsyncAbort` ve [Iclrtask2::endpreventasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) iç içe olamaz. Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptalleri gecikir. Bu çağrı çağrısıyla eşleştirilmiş değil, `EndPreventAsyncAbort` yöntemi, hangi iş parçacığı iptalleri olamaz teslim edilemiyor geçerli iş parçacığına bir duruma mümkün.  
  
 Gecikme kendisini durdurur bir iş parçacığı için dikkate alınır değil.  
  
 Bu özellik tarafından sunulan işlevselliği sanal makine (VM) tarafından dahili olarak kullanılır. Bu yöntemlerin kötüye VM'yi belirtilmeyen davranışlara neden olabilir. Örneğin, arama `EndPreventAsyncAbort` ilk çağırmadan `BeginPreventAsyncAbort` VM daha önce onu artar olduğunda Sayaç sıfıra ayarlanamıyor. Benzer şekilde, iç sayaç için taşma işaretlenmemiştir. Konak ve VM tarafından artırılır çünkü tam sayı sınırını aşarsa, bunun sonucunda oluşan davranışı belirtilmemiş.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [EndPreventAsyncAbort yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)  
 [Iclrtask2 arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [Iclrtaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Ihosttask arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Ihosttaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
