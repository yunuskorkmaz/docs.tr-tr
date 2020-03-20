---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176415"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain Yöntemi
Belirtilen yönetilen derlemede belirtilen türde belirtilen yöntemi çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzAssemblyPath`  
 [içinde] <xref:System.Reflection.Assembly> Kimin yönteminin <xref:System.Type> çağrılmasını tanımlayan yol.  
  
 `pwzTypeName`  
 [içinde] <xref:System.Type> Çağırmak için yöntemi tanımlayan adı.  
  
 `pwzMethodName`  
 [içinde] Çağırmak için yöntemin adı.  
  
 `pwzArgument`  
 [içinde] Yönteme geçmek için dize parametresi.  
  
 `pReturnValue`  
 [çıkış] Çağrılan yöntem tarafından döndürülen tümseci değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain`başarıyla döndürülür.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndürürse, CRL artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrılan yöntemaşağıdaki imzaya sahip olmalıdır:  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 çağrılan `pwzMethodName` yöntemin adını temsil eder `pwzArgument` ve bu yönteme parametre olarak geçen dize değerini temsil eder. HRESULT değeri S_OK olarak ayarlanırsa, `pReturnValue` çağrılan yöntem tarafından döndürülen tamsayı değerine ayarlanır. Aksi `pReturnValue` takdirde, ayarlanmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
