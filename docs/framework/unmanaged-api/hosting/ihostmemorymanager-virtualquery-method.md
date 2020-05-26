---
title: IHostMemoryManager::VirtualQuery Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
ms.openlocfilehash: 71c56b5dab2409be05e8260b1a2e39d28a709bba
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804375"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery Yöntemi
Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür. Win32 uygulamasının, `VirtualQuery` çağırma işleminin sanal adres alanındaki bir sayfa aralığı hakkında bilgi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `lpAddress`  
 'ndaki Sorgulanacak sanal bellekteki adrese yönelik bir işaretçi.  
  
 `lpBuffer`  
 dışı Belirtilen bellek bölgesi hakkında bilgi içeren bir yapıya yönelik işaretçi.  
  
 `dwLength`  
 'ndaki ' I işaret eden arabelleğin bayt cinsinden boyutu `lpBuffer` .  
  
 `pResult`  
 dışı Bilgi arabelleğinin döndürdüğü bayt sayısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`VirtualQuery`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `VirtualQuery`çağıran işlemin sanal adres alanındaki bir sayfa aralığı hakkında bilgi sağlar. Bu uygulama, `pResult` parametrenin değerini bilgi arabelleğinde döndürülen bayt sayısına ayarlar ve bır HRESULT değeri döndürür. Win32 `VirtualQuery` işlevinde, dönüş değeri arabellek boyutudur. Daha fazla bilgi için bkz. Windows platformu belgeleri.  
  
> [!IMPORTANT]
> İşletim sisteminin uygulamasının uygulanması kilitlenme gerektirmez `VirtualQuery` ve Kullanıcı kodunda askıya alınmış rastgele iş parçacıkları ile tamamlanmayı çalıştırabilir. Bu yöntemin barındırılan bir sürümünü uygularken harika bir uyarı kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
