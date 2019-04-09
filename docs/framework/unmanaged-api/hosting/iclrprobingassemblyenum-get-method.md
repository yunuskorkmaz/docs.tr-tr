---
title: ICLRProbingAssemblyEnum::Get Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 268462db51435b87194aafc374d5d8e8ec1df165
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079377"
---
# <a name="iclrprobingassemblyenumget-method"></a>ICLRProbingAssemblyEnum::Get Yöntemi
Belirtilen dizindeki derleme kimliğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwIndex`  
 [in] Derleme kimliği döndürmek için sıfır tabanlı dizini.  
  
 `pwzBuffer`  
 [out] Derlemeyi kimlik verilerini içeren arabellek.  
  
 `pcchBufferSize`  
 [out içinde] Boyutu `pwzBuffer` arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Get` başarıyla döndürüldü.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` çok küçüktür.|  
|ERROR_NO_MORE_ITEMS|Numaralandırma, daha fazla öğe içeriyor.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz. Herhangi bir barındırma yöntemini yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemci mimarisi için belirli kimlik dizin 0 konumunda kimliğidir. Microsoft Ara dilini (MSIL) mimarisi nötr bütünleştirilmiş kod dizin 1 kimliğidir. Dizin 2 konumunda kimlik mimarisi bilgi içerir.  
  
 `Get` genellikle iki kez çağrılır. İlk çağrı için bir null değer sağlayan `pwzBuffer`ve ayarlar `pcchBufferSize` boyuta uygun `pwzBuffer`. İkinci çağrı uygun şekilde boyutlandırılmış sağlayan `pwzBuffer`ve tamamlandıktan sonra derleme kurallı kimlik verilerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRProbingAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
