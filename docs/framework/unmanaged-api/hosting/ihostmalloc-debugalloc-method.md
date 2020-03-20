---
title: IHostMAlloc::DebugAlloc Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178031"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc Yöntemi
Ana bilgisayar, yığından belirtilen bellek miktarını ayırmasını ve ayrıca belleğin nereye tahsis edildiğini izlemesini ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cbSize`  
 [içinde] Geçerli bellek ayırma isteğinin baytboyutu.  
  
 `dwCriticalLevel`  
 [içinde] Bir ayırma hatasının etkisini gösteren [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) değerlerinden biri.  
  
 `pszFileName`  
 [içinde] Yürütülebilir kod dosyası debugged ediliyor.  
  
 `iLineNo`  
 [içinde] Ayırmanın istendiği `pszFileName` satır numarası.  
  
 `ppMem`  
 [çıkış] Ayrılan belleğe işaretçi veya istek tamamlanamadıysa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`başarıyla döndürülür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
|E_outofmemory|Ayırma isteğini tamamlamak için yeterli bellek yoktu.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR IHostMemoryManager arayarak bir [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) örnek için bir arayüz işaretçisi [alır::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) yöntemi. `DebugAlloc`hata ayıklama sırasında kullanılmak üzere kod dosyası bilgilerini almak için çalışma süresi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
