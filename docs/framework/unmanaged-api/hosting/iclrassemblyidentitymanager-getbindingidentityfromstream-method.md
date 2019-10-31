---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
ms.openlocfilehash: b30f6f5ce22290dc3750cef0171349ec5ff2f76a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126746"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Yöntemi
Belirtilen akıştaki derleme için kurallı derleme kimliği verilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStream`  
 'ndaki Değerlendirilecek derleme akışı.  
  
 `dwFlags`  
 'ndaki Gelecekteki genişletilebilirlik için verilmiştir. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.  
  
 `pwzBuffer`  
 dışı Donuk derleme kimliği verilerini içeren bir arabellek.  
  
 `pcchBufferSize`  
 [in, out] `pwzBuffer`boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|E_INVALIDARG|Sağlanan `pStream` null.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` boyutu çok küçük.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
