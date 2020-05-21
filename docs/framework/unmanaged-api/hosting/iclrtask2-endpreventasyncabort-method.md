---
title: ICLRTask2::EndPreventAsyncAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 3ea36c56ef9ccf5886ba96191627e5283da186f7
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762861"
---
# <a name="iclrtask2endpreventasyncabort-method"></a>ICLRTask2::EndPreventAsyncAbort Yöntemi
Geçerli iş parçacığında iş parçacığı iptaline neden olan yeni veya bekleyen iş parçacığı iptali isteklerinin yapılmasına izin verir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|HOST_E_INVALIDOPERATION|Yöntem, geçerli iş parçacığı olmayan bir iş parçacığında çağrıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemin çağrılması, geçerli iş parçacığı için gecikme iş parçacığı iptali sayacını bir azaltır.  
  
 [ICLRTask2:: Beginkoruyucu Tasyncabort](iclrtask2-beginpreventasyncabort-method.md) çağrısı yapın ve `EndPreventAsyncAbort` iç içe olabilir. Sayaç sıfırdan büyük olduğu sürece, geçerli iş parçacığı için iş parçacığı iptal işlemi gecikiyor.  
  
 Bu özellik tarafından açığa çıkarılan işlevsellik, sanal makine (VM) tarafından dahili olarak kullanılır. Bu yöntemlerin kötüye kullanılması, sanal makinede belirtilmeyen davranışa neden olabilir. Örneğin, `EndPreventAsyncAbort` ilk çağrılmadan çağırmak, `BeginPreventAsyncAbort` VM daha önce artmışsa sayacı sıfıra ayarlar. Benzer şekilde, iç sayaç taşma için denetlenmez. Hem konak hem de VM tarafından arttırılacağından, tam sayı sınırını aşarsa, ortaya çıkan davranış belirtilmemiş olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [BeginPreventAsyncAbort Yöntemi](iclrtask2-beginpreventasyncabort-method.md)
- [ICLRTask2 Arabirimi](iclrtask2-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
