---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3d5e53dd0845fbd01dbd9d20ce8feef12748c04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213929"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Yöntemi
Belirtilen dosya yolunda derleme için veri bağlama derleme kimliğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzFilePath`  
 [in] Değerlendirilecek dosyanın yolu.  
  
 `dwFlags`  
 [in] Değerini [Eclrassemblyıdentityflags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) bir derlemenin kimlik türü belirten sabit listesi. Sonra genişletilebilmek için sağlanır. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT ortak dil çalışma zamanı (CLR) sürüm 2. 0'ı destekleyen tek bir değerdir.  
  
 `pwzBuffer`  
 [out] Donuk derleme kimlik verilerini içeren arabellek.  
  
 `pcchBufferSize`  
 [out içinde] Bir işaretçinin boyutuna `pwzBuffer`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntemi başarıyla döndürüldü.|  
|E_INVALIDARG|Sağlanan `pwzFilePath` null.|  
|ERROR_INSUFFICIENT_BUFFER|Boyutu `pwzBuffer` çok küçük.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetBindingIdentityFromFile` genellikle iki kez çağrılır. İlk çağrı için bir null değer sağlayan `pwzBuffer`, ve yöntemi içinde uygun boyutta `pcchBufferSize`. İkinci çağrı uygun şekilde ayrılan bir arabellek sağlar ve tamamlandığında gerçek arabellek verilerle yöntemi döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRHostBindingPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
