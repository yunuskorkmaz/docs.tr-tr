---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: 8da9c9fea5cf5b3a27eeb9d0222f0845c832b7da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714204"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi

Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pwzSourceAssemblyIdentity`  
 'ndaki Değiştirilecek derlemenin kimliği.  
  
 `pwzTargetAssemblyIdentity`  
 'ndaki Değiştirilen derlemenin yeni kimliği.  
  
 `pbApplicationPolicy`  
 'ndaki Değiştirilecek derleme için bağlama ilkesi verilerini içeren bir arabelleğin işaretçisi.  
  
 `cbAppPolicySize`  
 'ndaki Değiştirilmekte olan bağlama ilkesinin boyutu.  
  
 `dwPolicyModifyFlags`  
 'ndaki Yeniden yönlendirme denetimini gösteren [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) DEĞERLERININ mantıksal veya birleşimi.  
  
 `pbNewApplicationPolicy`  
 dışı Yeni bağlama ilkesi verilerini içeren bir arabelleğin işaretçisi.  
  
 `pcbNewAppPolicySize`  
 [in, out] Yeni bağlama ilkesi arabelleğinin boyutuna yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İlke başarıyla değiştirildi.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity` ya da `pwzTargetAssemblyIdentity` null bir başvurudur.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` çok küçük.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ModifyApplicationPolicy`Yöntemi iki kez çağrılabilir. İlk çağrı, parametre için null değer sağlamalıdır `pbNewApplicationPolicy` . Bu çağrı için gerekli olan değer ile birlikte döndürülür `pcbNewAppPolicySize` . İkinci çağrı için bu değeri sağlamalı `pcbNewAppPolicySize` ve için bu boyut için bir arabellek göstermelidir `pbNewApplicationPolicy` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostBindingPolicyManager Arabirimi](iclrhostbindingpolicymanager-interface.md)
