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
ms.openlocfilehash: 505c16cb7ead7950b6d2d6d401730cc3368fb6aa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703300"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>ICLRRuntimeHost::ExecuteInAppDomain Yöntemi
<xref:System.AppDomain>Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `AppDomainId`  
 'ndaki Belirtilen metodun çalıştırılacağı sayısal KIMLIĞI <xref:System.AppDomain> .  
  
 `pCallback`  
 'ndaki Belirtilen içinde yürütülecek işleve yönelik bir işaretçi <xref:System.AppDomain> .  
  
 `cookie`  
 'ndaki Donuk, çağırana ayrılan belleğe yönelik bir işaretçi. Bu parametre, ortak dil çalışma zamanı (CLR) tarafından etki alanı geri çağırması ile geçirilir. Çalışma zamanı tarafından yönetilen yığın belleği değildir; Bu belleğin ayırma ve yaşam süresi çağıran tarafından denetlenir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ExecuteInAppDomain`Konağın, <xref:System.AppDomain> belirtilen yönetilen yöntemin üzerinde yürütülmesi gereken yönetilen yöntemi kontrol etmesine izin verir. <xref:System.AppDomain.Id%2A> [GetCurrentAppDomainId metodunu](iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, özelliğin değerine karşılık gelen bir uygulama etki alanı tanımlayıcısının değerini alabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeHost Arabirimi](iclrruntimehost-interface.md)
