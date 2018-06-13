---
title: ICLRRuntimeHost::ExecuteInAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96352ec5eaba67489dbef999925c56475611746c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435974"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>ICLRRuntimeHost::ExecuteInAppDomain Yöntemi
Belirtir <xref:System.AppDomain> belirtilen yönetilen kod yürütmek üzere.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AppDomainId`  
 [in] Sayısal kimliği <xref:System.AppDomain> belirtilen yöntem yürütmek üzere.  
  
 `pCallback`  
 [in] Belirtilen içinde yürütülecek işlevi için bir işaretçi <xref:System.AppDomain>.  
  
 `cookie`  
 [in] Donuk arayana ayrılan bellek için bir işaretçi. Bu parametre ortak dil çalışma zamanı tarafından (CLR) için etki alanı geri iletilir. Çalışma zamanı tarafından yönetilen yığın bellek olmadığı; ayırma ve bu bellek ömrü çağıran tarafından denetlenir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ExecuteInAppDomain` Denetim ana bilgisayar tanır yönetilen üzerinden <xref:System.AppDomain> belirtilen Yönetilen yöntemi içinde yürütülmelidir. Değerine karşılık gelen bir uygulama etki alanının tanımlayıcının değerini alabilir <xref:System.AppDomain.Id%2A> çağırarak özelliği, [Getcurrentappdomainıd yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
