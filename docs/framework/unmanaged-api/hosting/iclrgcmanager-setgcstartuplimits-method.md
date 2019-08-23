---
title: ICLRGCManager::SetGCStartupLimits Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29311f00f5ac4b61380b57cdd9fda07ec7de1b23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966200"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a>ICLRGCManager::SetGCStartupLimits Yöntemi
Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.  
  
> [!IMPORTANT]
> 4,5 .NET Framework başlayarak, segment boyutunu ve en fazla nesil 0 boyutunu [ICLRGCManager2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini kullanarak daha büyük `DWORD` değerlere ayarlayabilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `SegmentSize`  
 'ndaki Bir çöp toplama kesiminin belirtilen boyutu.  
  
 En küçük kesim boyutu 4 MB 'tır. Segmentler, 1 MB veya daha büyük artışlarla artırılabilir.  
  
 `MaxGen0Size`  
 'ndaki Oluşturma 0 için belirtilen en büyük boyut.  
  
 Minimum nesil 0 boyutu 64 KB 'tır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimits`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `SetGCStartupLimits` Ayarlayan değerler yalnızca bir kez belirtilebilir. Daha sonraki çağrıları `SetGCStartupLimits` yok sayılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MSCorEE. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Bellek Yönetimi](../../../standard/automatic-memory-management.md)
- [Atık Toplama](../../../standard/garbage-collection/index.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRGCManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
