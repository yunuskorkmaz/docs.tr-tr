---
title: "ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 018dc40895a79788a9eef20082d764db0b2265c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy Yöntemi
Bağlama ilkesi için belirtilen derlemeyi değiştirir ve ilke yeni bir sürümünü oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
 `pwzSourceAssemblyIdentity`  
 [in] Değiştirmek için derleme kimliği.  
  
 `pwzTargetAssemblyIdentity`  
 [in] Değiştirilen derleme yeni kimliği.  
  
 `pbApplicationPolicy`  
 [in] Veri bağlama ilkesini değiştirmek derleme içeren bir arabellek için bir işaretçi.  
  
 `cbAppPolicySize`  
 [in] Değiştirilecek bağlama ilkesi boyutu.  
  
 `dwPolicyModifyFlags`  
 [in] Mantıksal OR bileşimini [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) yeniden yönlendirme denetimini belirten değer.  
  
 `pbNewApplicationPolicy`  
 [out] Yeni bağlama ilke verilerini içeren bir arabellek için bir işaretçi.  
  
 `pcbNewAppPolicySize`  
 [içinde out] Yeni bağlama ilkesi arabellek boyutu için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İlke başarıyla değiştirildi.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`veya `pwzTargetAssemblyIdentity` null bir başvuru olduğundan.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy`çok küçüktür.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ModifyApplicationPolicy` Yöntemi iki kez çağrılabilir. İlk çağrı için boş bir değer sağlamanız `pbNewApplicationPolicy` parametresi. Bu çağrı için gerekli değerle döndürülecek `pcbNewAppPolicySize`. Bu değer için ikinci çağrı sağlamanız `pcbNewAppPolicySize`ve bu boyut için bir arabellek noktasına `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRHostBindingPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
