---
title: ICLRTask2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124520"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 Arabirimi
[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabiriminin tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginPreventAsyncAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Geçerli iş parçacığında yeni iş parçacığı iptali isteklerini geciktirir.|  
|[EndPreventAsyncAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni veya bekleyen iş parçacığı iptali isteklerinin yapılmasına izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICLRTask2` arabirimi `ICLRTask` arabirimini devralır ve başarısız olması gereken bir kod bölgesini korumak için konağın iş parçacığı iptal işlemini geciktirmesini sağlayan yöntemler ekler. `BeginPreventAsyncAbort` çağrısı, geçerli iş parçacığı için Gecikmeli iş parçacığı iptali sayacını artırır ve çağırma `EndPreventAsyncAbort` çağırır. `BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` çağrıları iç içe olabilir. Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.  
  
 `BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` çağrıları eşlenmezse, iş parçacığının iptal edilmesi durumunda geçerli iş parçacığına teslim edilemez durumuna ulaşmak mümkündür.  
  
 Gecikme, kendisini iptal eden bir iş parçacığı için kabul edilmez.  
  
 Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır. Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir. Örneğin, önce `BeginPreventAsyncAbort` çağrılmadan `EndPreventAsyncAbort` çağırmak, VM daha önce artmışsa sayacı sıfıra ayarlayabilir. Benzer şekilde, iç sayaç taşma için denetlenmez. Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.  
  
 `ICLRTask` devralınan Üyeler ve bu arabirimin diğer kullanımları hakkında daha fazla bilgi için [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabirimine bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
