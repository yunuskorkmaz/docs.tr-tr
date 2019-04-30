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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028ca0b9cb917d3e6cc0242cbc8c3f4a5a19ab39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760109"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery Yöntemi
Karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar. Win32 uygulaması `VirtualQuery` sayfaları çağırma işleminin sanal adres alanı içinde bir dizi hakkındaki bilgileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `lpAddress`  
 [in] Sorgulanacak sanal bellek adresi için bir işaretçi.  
  
 `lpBuffer`  
 [out] Belirtilen bellek bölgesini hakkında bilgi içeren bir yapıya bir işaretçi.  
  
 `dwLength`  
 [in] Arabelleğin bayt cinsinden boyutu, `lpBuffer` işaret eder.  
  
 `pResult`  
 [out] Bilgi arabellek tarafından döndürülen bayt sayısı için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `VirtualQuery` sayfalar çağırma işleminin sanal adres alanı aralığı hakkında bilgi sağlar. Bu uygulama ayarlar `pResult` bayt sayısı'için parametre bilgileri arabellekte ve HRESULT değerini döndürür. Win32'de `VirtualQuery` işlev, dönüş değeri, arabellek boyutu. Daha fazla bilgi için Windows Platform belgelerine bakın.  
  
> [!IMPORTANT]
>  İşletim sistemi uygulaması `VirtualQuery` kilitlenme tabi değildir ve rastgele iş parçacıkları askıya kullanıcı kodunda tamamlanana kadar çalıştırabilirsiniz. Bu yöntem barındırılan bir sürümünü uygularken harika dikkatli kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
