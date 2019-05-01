---
title: ICLRGCManager::Collect Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1746527a2667676dfeab89e72874204460bcd33c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984730"
---
# <a name="iclrgcmanagercollect-method"></a>ICLRGCManager::Collect Yöntemi
Bir çöp toplama işlemi için belirtilen oluşturmanın zorlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `Generation`  
 [in] Toplanacak oluşturma. -1 değeri, tüm nesillerdeki koleksiyonunu zorlar.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Collect` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Collect` Yöntem CLR'nin çöp toplayıcı, bir koleksiyon geçerli durumunda ne olursa olsun gerçekleştirmek için zorlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Bellek Yönetimi](../../../../docs/standard/automatic-memory-management.md)
- [Atık Toplama](../../../../docs/standard/garbage-collection/index.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRGCManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
