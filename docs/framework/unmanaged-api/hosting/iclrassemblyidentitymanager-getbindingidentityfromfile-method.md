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
ms.openlocfilehash: 5b537d59014afa783d3f8c5046cc02dad7ea7740
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616001"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Yöntemi
Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Bir derlemenin kimlik türünü gösteren [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) numaralandırması değeri. Gelecekteki genişletilebilirlik için verilmiştir. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanı (CLR) sürüm 2,0 ' nin desteklediği tek değerdir.  
  
 `pwzBuffer`  
 dışı Donuk derleme kimliği verilerini içeren bir arabellek.  
  
 `pcchBufferSize`  
 [in, out] Boyutu için bir işaretçi `pwzBuffer` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|E_INVALIDARG|Sağlanan `pwzFilePath` değer null.|  
|ERROR_INSUFFICIENT_BUFFER|Boyutu `pwzBuffer` çok küçük.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetBindingIdentityFromFile`genellikle iki kez çağırılır. İlk çağrı için null bir değer sağlar `pwzBuffer` ve yöntemi içinde uygun boyutu döndürür `pcchBufferSize` . İkinci çağrı uygun bir ayrılmış arabellek sağlar ve Yöntem tamamlandığında gerçek arabellek verileriyle birlikte döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [ICLRHostBindingPolicyManager Arabirimi](iclrhostbindingpolicymanager-interface.md)
