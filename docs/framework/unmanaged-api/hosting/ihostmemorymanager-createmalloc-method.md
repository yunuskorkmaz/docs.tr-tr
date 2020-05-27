---
title: IHostMemoryManager::CreateMAlloc Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
ms.openlocfilehash: 89c1d7b043d4369bf16a851924711c3c9d75791e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804525"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a>IHostMemoryManager::CreateMAlloc Yöntemi
Ana bilgisayar tarafından oluşturulan bir yığından gelen ayırma isteklerini oluşturmak için kullanılan bir [IHostMAlloc](ihostmalloc-interface.md) örneğine yönelik bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwMallocType`  
 'ndaki Ayrılmakta olan belleğin özelliklerini belirten [MALLOC_TYPE](malloc-type-enumeration.md) bayraklarının birleşimi.  
  
 `ppMAlloc`  
 dışı Konak tarafından sağlanmış bir örneğin adresine yönelik bir işaretçi `IHostMAlloc` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CreateMAlloc`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|Ayırma isteğini tamamlamaya yetecek kadar fiziksel bellek yoktu.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateMAlloc`CLR 'nin standart Win32 işlevlerini kullanmak yerine ana bilgisayar aracılığıyla ayırma istekleri yapmasına izin veren bir nesne döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMalloc Arabirimi](ihostmalloc-interface.md)
- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
