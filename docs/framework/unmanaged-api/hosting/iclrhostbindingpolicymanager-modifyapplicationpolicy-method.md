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
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178096"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi
Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 [içinde] Değiştirilen derlemenin kimliği.  
  
 `pwzTargetAssemblyIdentity`  
 [içinde] Değiştirilen derlemenin yeni kimliği.  
  
 `pbApplicationPolicy`  
 [içinde] Derlemenin değiştirilen bağlama ilkesi verilerini içeren arabelleğe işaretçi.  
  
 `cbAppPolicySize`  
 [içinde] Değiştirilecek bağlama ilkesinin boyutu.  
  
 `dwPolicyModifyFlags`  
 [içinde] [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) değerlerinin mantıksal veya birleşimi, yeniden yönlendirme denetimini gösterir.  
  
 `pbNewApplicationPolicy`  
 [çıkış] Yeni bağlama ilkesi verilerini içeren bir arabellek için bir işaretçi.  
  
 `pcbNewAppPolicySize`  
 [içinde, dışarı] Yeni bağlama ilkesi arabelleği boyutuna bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İlke başarıyla değiştirildi.|  
|E_ınvalıdarg|`pwzSourceAssemblyIdentity`ya `pwzTargetAssemblyIdentity` da null bir referans oldu.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy`çok küçük.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndükten sonra, CLR artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem `ModifyApplicationPolicy` iki kez çağrılabilir. İlk çağrı `pbNewApplicationPolicy` parametre için null bir değer sağlamalıdır. Bu çağrı için `pcbNewAppPolicySize`gerekli değer ile dönecektir. İkinci çağrı için `pcbNewAppPolicySize`bu değeri sağlamalı ve bu boyuttabir `pbNewApplicationPolicy`arabelleğe işaret etmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostBindingPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
