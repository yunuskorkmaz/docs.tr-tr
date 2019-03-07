---
title: IHostMemoryManager::VirtualAlloc Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e5ce46e1cf034e6b86d738d8ec69332df1ff9fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486270"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc Yöntemi
Karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar. Win32 uygulaması `VirtualAlloc` ayırır veya çağırma işleminin sanal adres alanı sayfalarında bölgesi kaydeder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAddress`  
 [in] Başlangıç adresi ayırmak için bölge için bir işaretçi.  
  
 `dwSize`  
 [in] Alanının bayt cinsinden boyutu.  
  
 `flAllocationType`  
 [in] Bellek ayırma türü.  
  
 `flProtect`  
 [in] Sayfaların ayrılacak bellek koruması bölge için.  
  
 `dwCriticalLevel`  
 [in] Bir [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) ayırma hatası etkisini gösteren değer.  
  
 `ppMem`  
 [out] Başlangıç adresi ayrılmış bellek ya da istek karşılanmadı, null işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|Ayırma isteğinin tamamlanması yeterli bellek yoktu|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bölge çağırarak işleminizi adres alanında ayırmak `VirtualAlloc`. `pAddress` Parametresi istediğiniz bellek bloğu başlangıç adresini içerir. Bu parametre genellikle null. İşletim sistemi süreciniz için kullanılabilir boş adres aralıkları kaydını tutar. A `pAddress` null değerini uygun gördüğü her yerde bölge ayırmak için sistemi bildirir. Alternatif olarak, belirli bir başlangıç adresi için bellek bloğu sağlayabilir. Her iki durumda da çıkış parametresi `ppMem` bir işaretçi olarak ayrılmış belleği döndürülür. İşlevi, bir HRESULT değerini döndürür.  
  
 Win32 `VirtualAlloc` işlevi yok bir `ppMem` parametresi ve ayrılan bellek için bunun yerine bir işaretçi döndürür. Daha fazla bilgi için Windows Platform belgelerine bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
