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
ms.openlocfilehash: 90ce4e888ddb3a10dd0dfd7e68463311db86742f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677771"
---
# <a name="iclrgcmanagercollect-method"></a>ICLRGCManager::Collect Yöntemi

Belirtilen oluşturma için bir çöp toplamayı zorlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `Generation`  
 'ndaki Toplanacak oluşturma. -1 değeri, tüm nesiller koleksiyonunu zorlar.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Collect` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `Collect`Yöntemi, clr 'nin çöp toplayıcısının geçerli durumundan bağımsız olarak bir koleksiyon gerçekleştirmesini zorlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik bellek yönetimi](../../../standard/automatic-memory-management.md)
- [Çöp toplama](../../../standard/garbage-collection/index.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [ICLRGCManager Arabirimi](iclrgcmanager-interface.md)
- [CLR Barındırma Arabirimleri](clr-hosting-interfaces.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
