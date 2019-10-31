---
title: IHostMemoryManager::VirtualFree Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
ms.openlocfilehash: b53c0bb38922ae8de048c131807eb32f97423d6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128586"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree Yöntemi
Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür. `VirtualFree` Win32 uygulamasının, çağıran işlemin sanal adres alanı içindeki bir sayfa bölgesini yayınlar, serbest bırakır veya yayınlar ve kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `lpAddress`  
 'ndaki Boşaltılacak sanal bellek sayfalarının temel adresine yönelik bir işaretçi.  
  
 `dwSize`  
 'ndaki Boşaltılacak bölgenin bayt cinsinden boyutu.  
  
 `dwFreeType`  
 'ndaki Boşaltma işleminin türü.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`VirtualFree` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_INVALIDOPERATION|Ana bilgisayar aracılığıyla ayrılmamış belleği serbest bırakma girişiminde bulunuldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 `VirtualFree`, [IHostMemoryManager:: VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) işlevine daha önceki bir çağrı yoluyla `lpAddress` parametresiyle ilişkili sanal bellek sayfalarını serbest bırakır. Ana bilgisayar üzerinden ayrılmamış belleği serbest bırakma denemeleri HOST_E_INVALIDOPERATION döndürmelidir.  
  
 Semantiği `VirtualFree`Win32 uygulamasıyla aynıdır. Daha fazla bilgi için bkz. Windows platformu belgeleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
