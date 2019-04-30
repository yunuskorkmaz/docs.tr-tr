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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518248651de6d8afdf25692c5f48da52b11eb0f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763405"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 Arabirimi
Tüm işlevlerini sağlar [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabirim; Ayrıca, iş parçacığı iptalleri geçerli iş parçacığında geciktirileceği tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginPreventAsyncAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Gecikmeler yeni iş parçacığı geçerli iş parçacığı isteklerinde durdurur.|  
|[EndPreventAsyncAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Yeni izin verir veya bekleyen iş parçacığı elde etmek iş parçacığı durdurma isteği geçerli iş parçacığı üzerinde durdurur.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICLRTask2` Arabirimi devralır `ICLRTask` arabirim ve konak değil başarısız olması gereken bir bölgesine korumak için iş parçacığı iptalleri, gecikme sağlayan bir yöntem ekler. Çağırma `BeginPreventAsyncAbort` geçerli iş parçacığı ve arama için gecikme iş parçacığı iptal sayaç artırılır `EndPreventAsyncAbort` azaltır. Çağrılar `BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` yuvalanabilir. Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptalleri gecikir.  
  
 Varsa çağrılar `BeginPreventAsyncAbort` ve `EndPreventAsyncAbort` olan eşleştirilmedi, hangi iş parçacığı iptalleri olamaz teslim edilemiyor geçerli iş parçacığına bir durumuna ulaşmasını sağlamak mümkündür.  
  
 Gecikme kendisini iptal ettiğinde bir iş parçacığı için uygulanır değil.  
  
 Bu özellik tarafından sunulan işlevselliği, sanal makine (VM) tarafından dahili olarak kullanılır. Bu yöntemlerin kötüye, VM'yi belirsiz davranışa neden olabilir. Örneğin, çağırma `EndPreventAsyncAbort` ilk çağırmadan `BeginPreventAsyncAbort` sayaç VM daha önce artan olduğunda sıfır olarak ayarlayabilirsiniz. Benzer şekilde, iç sayaç için taşma işaretlenmemiştir. Hem konak hem de VM tarafından artar çünkü tam sayı sınırını aşarsa, sonuçta ortaya çıkan davranış belirtilmemiş.  
  
 Devralınan üyeleri hakkında bilgi için `ICLRTask` ve diğer kullanımlar bu arabirimin hakkında [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) arabirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
