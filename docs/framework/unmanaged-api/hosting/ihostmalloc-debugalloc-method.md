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
ms.openlocfilehash: 8475362ede5ea28009d5abc54c286d6f2a6fed0f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804631"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc Yöntemi
Konağın yığından belirtilen miktarda bellek ayırmasını ve ayrıca belleğin nerede ayrıldığını izlemelerini ister.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Geçerli bellek ayırma isteğinin bayt cinsinden boyutu.  
  
 `dwCriticalLevel`  
 'ndaki Bir ayırma hatasının etkisini belirten [Ememorycriticalhandle düzey](ememorycriticallevel-enumeration.md) değerlerinden biri.  
  
 `pszFileName`  
 'ndaki Hata ayıklanan yürütülebilir dosyanın kod dosyası.  
  
 `iLineNo`  
 'ndaki Ayırmanın istendiği satır numarası `pszFileName` .  
  
 `ppMem`  
 dışı Ayrılan belleğe yönelik bir işaretçi veya istek tamamlanmayabilir null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|Ayırma isteğini tamamlamaya yetecek miktarda bellek yoktu.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR [IHostMemoryManager:: Createmayırma](ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) örneğine bir arabirim işaretçisi alır. `DebugAlloc`çalışma zamanının hata ayıklama sırasında kullanılmak üzere kod dosyası bilgilerini almasına izin verir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
- [IHostMalloc Arabirimi](ihostmalloc-interface.md)
