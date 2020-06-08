---
title: ICLRPolicyManager::SetTimeoutAndAction Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: 02e836601be72d54f561e077cd3c466470bafb25
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504101"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a>ICLRPolicyManager::SetTimeoutAndAction Yöntemi
Belirtilen işlem için bir zaman aşımı değeri ayarlar ve işlem gerçekleştiğinde ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `operation`  
 'ndaki Zaman aşımı ve ilke ayarlanacak işlemi belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri `action` . Aşağıdaki değerler desteklenir:  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `dwMilliseconds`  
 'ndaki Milisaniye cinsinden yeni zaman aşımı değeri. Sonsuz değeri `operation` hiçbir zaman zaman aşımına uğramamasını sağlar.  
  
 `action`  
 'ndaki CLR 'nin gerçekleştiğinde yapması gereken ilke eylemini gösteren [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri `operation` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetTimeoutAndAction`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|Belirtilen için bir zaman aşımı ayarlanamaz `operation` veya geçersiz bir değer sağlandı `action` .|  
  
## <a name="remarks"></a>Açıklamalar  
 `SetTimeoutAndAction`[ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) ve [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) yöntemlerinin yeteneklerini kapsüller ve bu iki yönteme sıralı çağrılar yerine çağrılabilir.  
  
> [!IMPORTANT]
> Tüm ilke eylemi değerleri CLR işlemleri için zaman aşımı davranışı olarak belirtilemez. Geçerli değerler için bu iki yöntem için konuların açıklamalar bölümlerine bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrOperation Sabit Listesi](eclroperation-enumeration.md)
- [EPolicyAction Sabit Listesi](epolicyaction-enumeration.md)
- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
- [SetActionOnTimeout Yöntemi](iclrpolicymanager-setactionontimeout-method.md)
- [ICLRPolicyManager:: Settimeoutandadction](iclrpolicymanager-settimeoutandaction-method.md)
