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
ms.openlocfilehash: 19d6a76d62680be91a7b9721912ca528edde7511
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126749"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Yöntemi
Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzFilePath`  
 'ndaki Değerlendirilecek dosyanın yolu.  
  
 `dwFlags`  
 'ndaki Bir derlemenin kimlik türünü gösteren [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) numaralandırması değeri. Gelecekteki genişletilebilirlik için verilmiştir. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanı (CLR) sürüm 2,0 ' nin desteklediği tek değerdir.  
  
 `pwzBuffer`  
 dışı Donuk derleme kimliği verilerini içeren bir arabellek.  
  
 `pcchBufferSize`  
 [in, out] `pwzBuffer`boyutuna yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|E_INVALIDARG|Sağlanan `pwzFilePath` null.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` boyutu çok küçük.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetBindingIdentityFromFile` genellikle iki kez çağırılır. İlk çağrı `pwzBuffer`için null değer sağlar ve Yöntem `pcchBufferSize`uygun boyutu döndürür. İkinci çağrı uygun bir ayrılmış arabellek sağlar ve Yöntem tamamlandığında gerçek arabellek verileriyle birlikte döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRHostBindingPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
