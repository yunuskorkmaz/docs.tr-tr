---
description: ': Iclriocompletionmanager:: Ontamamlanan yöntem hakkında daha fazla bilgi edinin'
title: ICLRIoCompletionManager::OnComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: d54b189debdfc2959676b53fd3fb51b2c10dce17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789896"
---
# <a name="iclriocompletionmanageroncomplete-method"></a>ICLRIoCompletionManager::OnComplete Yöntemi

[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine bir çağrı kullanılarak yapılan bir g/ç isteğinin durumunun ortak dil çalışma zamanına (CLR) bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwErrorCode`  
 'ndaki Bağlama işleminin durumunu gösteren bir HRESULT değeri.  
  
- S_OK işlemin başarıyla tamamlandığını gösterir.  
  
- HOST_E_INTERRUPTED, çağrının tamamlanmadan sona erdirildiğini gösterir.  
  
- E_FAIL bilinmeyen, kurtarılamaz ve çok zararlı bir hatanın oluştuğunu gösterir.  
  
 `NumberOfBytesTransferred`  
 'ndaki G/ç isteğinin işlenmesi sırasında aktarılan baytların sayısı.  
  
 `pvOverlapped`  
 'ndaki `OVERLAPPED` Yöntemine yapılan çağrıya geçirilen yapıya yönelik bir işaretçi `IHostIoCompletionManager::Bind` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`OnComplete` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 Ana bilgisayar bir g/ç tamamlama soyutlama uygularsa, CLR, [ıhostiocompletionmanager](ihostiocompletionmanager-interface.md)yöntemlerini kullanarak ana bilgisayar aracılığıyla g/ç istekleri yapar. Daha sonra ana bilgisayar, `OnComplete` Bu tür isteklerin sonucunun çalışma zamanına bildirmek için yöntemini çağırır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager Arabirimi](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager Arabirimi](ihostthreadpoolmanager-interface.md)
