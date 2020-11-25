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
ms.openlocfilehash: a2deabc5f1c7ea0f42b6d8ec3944d984854ae571
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731286"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc Yöntemi

Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür. Win32 uygulamasının, `VirtualAlloc` çağıran işlemin sanal adres alanındaki bir sayfa bölgesini ayırır veya kaydeder.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
 'ndaki Ayrılacak bölgenin başlangıç adresine yönelik bir işaretçi.  
  
 `dwSize`  
 'ndaki Bölgenin bayt cinsinden boyutu.  
  
 `flAllocationType`  
 'ndaki Bellek ayırma türü.  
  
 `flProtect`  
 'ndaki Ayrılacak sayfa bölgesi için bellek koruması.  
  
 `dwCriticalLevel`  
 'ndaki Bir ayırma hatasının etkisini gösteren bir [Ememorycriticalhandle düzeyi](ememorycriticallevel-enumeration.md) değeri.  
  
 `ppMem`  
 dışı Ayrılan belleğin başlangıç adresine yönelik işaretçi veya istek karşılanmıyorsa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu|  
  
## <a name="remarks"></a>Açıklamalar  

 ' İ çağırarak, işleminizin adres alanında bir bölgeyi ayırabilirsiniz `VirtualAlloc` . Parametresi, istediğiniz `pAddress` bellek bloğunun başlangıç adresini içerir. Bu parametre genellikle null olarak ayarlanır. İşletim sistemi, işlem için kullanılabilen boş adres aralıklarının bir kaydını tutar. `pAddress`Null değeri, sisteme uygun olduğu yerde bölge ayırmasını sağlar. Alternatif olarak, bellek bloğu için belirli bir başlangıç adresi sağlayabilirsiniz. Her iki durumda da, çıkış parametresi `ppMem` ayrılan belleğe bir işaretçi olarak döndürülür. İşlevin kendisi bir HRESULT değeri döndürür.  
  
 Win32 `VirtualAlloc` işlevinin bir `ppMem` parametresi yoktur ve bunun yerine, ayrılan belleğe işaretçiyi döndürür. Daha fazla bilgi için bkz. Windows platformu belgeleri.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
