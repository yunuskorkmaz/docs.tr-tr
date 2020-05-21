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
ms.openlocfilehash: b067ca72e030bce24a7efde5e3488a00024e9613
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762875"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 Arabirimi
[ICLRTask](iclrtask-interface.md) arabiriminin tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginPreventAsyncAbort Yöntemi](iclrtask2-beginpreventasyncabort-method.md)|Geçerli iş parçacığında yeni iş parçacığı iptali isteklerini geciktirir.|  
|[EndPreventAsyncAbort Yöntemi](iclrtask2-endpreventasyncabort-method.md)|Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni veya bekleyen iş parçacığı iptali isteklerinin yapılmasına izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICLRTask2`Arabirim, arabirimi devralır `ICLRTask` ve başarısız olması gereken bir kod bölgesini korumak için konağın iş parçacığı iptal işlemini geciktirmesini sağlayan yöntemler ekler. Çağırma, `BeginPreventAsyncAbort` geçerli iş parçacığı için gecikme-iş parçacığı iptali sayacını artırır ve bu çağrıyı `EndPreventAsyncAbort` azaltır. Ve için `BeginPreventAsyncAbort` çağrıları `EndPreventAsyncAbort` iç içe olabilir. Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.  
  
 Ve ' a `BeginPreventAsyncAbort` çağrıları `EndPreventAsyncAbort` eşlenmediğinde, iş parçacığı durdurulduğunda geçerli iş parçacığına teslim edilemeyen bir duruma ulaşmak mümkündür.  
  
 Gecikme, kendisini iptal eden bir iş parçacığı için kabul edilmez.  
  
 Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır. Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir. Örneğin, `EndPreventAsyncAbort` ilk çağrılmadan çağırmak, `BeginPreventAsyncAbort` VM daha önce artmışsa sayacı sıfıra ayarlar. Benzer şekilde, iç sayaç taşma için denetlenmez. Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.  
  
 Kaynağından devralınan Üyeler `ICLRTask` ve bu arabirimin diğer kullanımları hakkında daha fazla bilgi Için [ICLRTask](iclrtask-interface.md) arabirimine bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
