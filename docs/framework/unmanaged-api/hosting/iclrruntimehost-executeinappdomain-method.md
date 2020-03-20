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
ms.openlocfilehash: c012e4e2b5e41737f7bbe6a0fb887693b0ba22c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176428"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>ICLRRuntimeHost::ExecuteInAppDomain Yöntemi
Belirtilen yönetilen <xref:System.AppDomain> kodun yürütülmek için hangi sini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `AppDomainId`  
 [içinde] Belirtilen yöntemin <xref:System.AppDomain> yürütülmesi için sayısal kimlik.  
  
 `pCallback`  
 [içinde] Belirtilen <xref:System.AppDomain>içinde yürütmek için işlev için bir işaretçi .  
  
 `cookie`  
 [içinde] Opak arayan ayrılmış bellek için bir işaretçi. Bu parametre ortak dil çalışma süresi (CLR) tarafından etki alanı geri arama geçirilir. Çalışma zamanı yönetilen yığın belleği değildir; bu belleğin hem tahsisi hem de kullanım ömrü arayan tarafından denetlenir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain`başarıyla döndürülür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ExecuteInAppDomain`ev sahibinin, belirtilen yönetilen <xref:System.AppDomain> yöntemin hangi şekilde yönetildiği üzerinde yürütülmesi gerektiğini denetlemesini sağlar. <xref:System.AppDomain.Id%2A> [GetCurrentAppDomainId Yöntemi'ni](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)arayarak, bir uygulama etki alanının özelliğinin değerine karşılık gelen tanımlayıcısının değerini alabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
