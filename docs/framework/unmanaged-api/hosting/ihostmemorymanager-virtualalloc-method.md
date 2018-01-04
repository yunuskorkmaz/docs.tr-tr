---
title: "IHostMemoryManager::VirtualAlloc Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 761958c44ad374d522a52826929e320e65957ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc Yöntemi
Karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür. Win32 uygulaması `VirtualAlloc` ayırır ya da bir bölge çağırma işleminin sanal adres alanındaki sayfaların kaydeder.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `pAddress`  
 [in] Başlangıç adresi ayırmak için bölge için bir işaretçi.  
  
 `dwSize`  
 [in] Bölgenin bayt cinsinden boyutu.  
  
 `flAllocationType`  
 [in] Bellek ayırma türü.  
  
 `flProtect`  
 [in] Bölge için bellek koruma ayrılması sayfaların.  
  
 `dwCriticalLevel`  
 [in] Bir [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) ayırma hatası etkisini belirten değer.  
  
 `ppMem`  
 [out] Başlangıç adresi isteği uyulmadığını yoksa null değerini veya ayrılmış bellek işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|Ayırma isteği tamamlamak yeterli bellek yoktu|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bölge çağırarak işleminizi adres alanı ayırmak `VirtualAlloc`. `pAddress` Parametresi istediğiniz bellek bloğu başlangıç adresini içerir. Bu parametre genellikle null. İşletim sistemi bir kayıt işlemi için kullanılabilir boş adres aralıklarının tutar. A `pAddress` null değeri görür uygun yerlerde bölge ayrılacak sistem bildirir. Alternatif olarak, belirli bir başlangıç adresi için bellek bloğu sağlayabilir. Her iki durumda da çıkış parametresi `ppMem` işaretçi olarak ayrılan belleği döndürülür. İşlevi bir HRESULT değerini döndürür.  
  
 Win32 `VirtualAlloc` işlevi yok bir `ppMem` parametresi ve bunun yerine ayrılmış bellek işaretçisi döndürür. Daha fazla bilgi için Windows platformu belgelerine bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
