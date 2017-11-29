---
title: IHostIoCompletionManager::GetHostOverlappedSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetHostOverlappedSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6633e0271f29d44bb1d14495d80ffdf9868485a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize Metodu
G/ç istekleri eklemek için ana bilgisayar oranla herhangi bir özel veri boyutunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pcbSize`  
 [out] Ortak dil çalışma zamanı (CLR) Win32 boyuta ek olarak ayırmalısınız bayt sayısı için bir işaretçi `OVERLAPPED` nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Win32 Windows Platform API'leri tüm zaman uyumsuz g/ç çağrıları ele `OVERLAPPED` nesnesini dosya işaretçisini konumu gibi bilgiler sağlar. Zaman uyumsuz g/ç genellikle aramalarda uygulamaları durumunu korumak üzere yapısına özel veri ekleyin. `GetHostOverlappedSize`ve [Ihostıocompletionmanager::ınitializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) gibi özel verileri dahil etmek ana bilgisayar için bir fırsattır.  
  
 CLR çağrıları `GetHostOverlappedSize` eklemek için ana bilgisayar oranla özel veri boyutunu belirlemek için yöntemi `OVERLAPPED` nesnesi.  
  
> [!NOTE]
>  `GetHostOverlappedSize`yalnızca bir kez çağrılır. Ana bilgisayarın özel veri her g/ç istek için aynı boyutta olmalıdır.  
  
> [!IMPORTANT]
>  Boyutunu `OVERLAPPED` nesnenin kendisini değerinde eklenmedi `pcbSize`.  
  
 Hakkında daha fazla bilgi için `OVERLAPPED` yapısı, Windows platformu belgelerine bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.NativeOverlapped>  
 [Iclrıocompletionmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [Ihostıocompletionmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
