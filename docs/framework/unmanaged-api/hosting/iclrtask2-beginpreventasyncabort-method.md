---
title: ICLRTask2::BeginPreventAsyncAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a43fef7f6dfa6dbe0bb9f1c4caec2c9c224b93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213590"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a>ICLRTask2::BeginPreventAsyncAbort Yöntemi
Yeni iş parçacığı gecikmeler geçerli iş parçacığında iş parçacığı iptalleri výsledek isteklerinin durdurur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HOST_E_INVALIDOPERATION|Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemi çağırmadan geçerli iş parçacığına gecikme iş parçacığı iptal sayaç bire artırır.  
  
 Çağrılar `BeginPreventAsyncAbort` ve [Iclrtask2::endpreventasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) yuvalanabilir. Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptalleri gecikir. Bu çağrı bir çağrı ile eşleştirilmiş değil, `EndPreventAsyncAbort` yöntemi mümkündür hangi iş parçacığı iptalleri olamaz teslim edilemiyor geçerli iş parçacığına bir duruma ulaşmak.  
  
 Gecikme kendisini iptal ettiğinde bir iş parçacığı için uygulanır değil.  
  
 Bu özellik tarafından sunulan işlevselliği, sanal makine (VM) tarafından dahili olarak kullanılır. Bu yöntemlerin kötüye, VM'yi belirsiz davranışa neden olabilir. Örneğin, çağırma `EndPreventAsyncAbort` ilk çağırmadan `BeginPreventAsyncAbort` sayaç VM daha önce artan olduğunda sıfır olarak ayarlayabilirsiniz. Benzer şekilde, iç sayaç için taşma işaretlenmemiştir. Hem konak hem de VM tarafından artar çünkü tam sayı sınırını aşarsa, sonuçta ortaya çıkan davranış belirtilmemiş.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EndPreventAsyncAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [ICLRTask2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
