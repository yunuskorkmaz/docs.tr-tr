---
title: ICLRHostBindingPolicyManager::EvaluatePolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
ms.openlocfilehash: f72a66354bfc907dab7ebc24de515bdfb20ddfb2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703600"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a>ICLRHostBindingPolicyManager::EvaluatePolicy Yöntemi
Bağlama ilkesini konak adına değerlendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzReferenceIdentity`  
 'ndaki İlke değerlendirmesinden önce derlemeye bir başvuru.  
  
 `pbApplicationPolicy`  
 'ndaki İlke verilerini içeren bir arabelleğin işaretçisi.  
  
 `cbAppPolicySize`  
 'ndaki `pbApplicationPolicy`Arabelleğin boyutu.  
  
 `pwzPostPolicyReferenceIdentity`  
 dışı Yeni ilke verileri değerlendirmesinden sonra derlemeye bir başvuru.  
  
 `pcchPostPolicyReferenceIdentity`  
 [in, out] Yeni ilke verilerinin değerlendirilmesinden sonra, derleme kimliği başvuru arabelleğinin boyutuna yönelik bir işaretçi.  
  
 `pdwPoliciesApplied`  
 dışı Hangi ilkelerin uygulandığını belirten, [EBindPolicyLevels](ebindpolicylevels-enumeration.md) DEĞERLERININ mantıksal veya birleşimine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Değerlendirme başarıyla tamamlandı.|  
|E_INVALIDARG|`pwzReferenceIdentity`Ya da `pbApplicationPolicy` null bir başvurudur.|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize`çok küçük.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `EvaluatePolicy`Yöntemi, konağın konağa özgü derleme sürümü oluşturma gereksinimlerini korumak için bağlama ilkesini etkilemesini sağlar. İlke altyapısının kendisi CLR içinde kalır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostBindingPolicyManager Arabirimi](iclrhostbindingpolicymanager-interface.md)
