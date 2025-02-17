---
description: ': ICLRPolicyManager:: SetActionOnTimeout yöntemi hakkında daha fazla bilgi edinin'
title: ICLRPolicyManager::SetActionOnTimeout Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: d682acd49bdc4fa0f8c58a1300e2215816fe2718
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689033"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a>ICLRPolicyManager::SetActionOnTimeout Yöntemi

Belirtilen işlem zaman aşımına uğrarsa ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `operation`  
 'ndaki Zaman aşımı eyleminin belirtme işlemini belirten [EClrOperation](eclroperation-enumeration.md) değerlerinden biri. Aşağıdaki değerler desteklenir:  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `action`  
 'ndaki İşlem zaman aşımına uğrarsa gerçekleştirilecek ilke eylemini gösteren [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetActionOnTimeout` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|Belirtilen için bir zaman aşımı ayarlanamaz `operation` veya geçersiz bir değer sağlandı `operation` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Zaman aşımı değeri, CLR tarafından ayarlanan varsayılan zaman aşımı ya da [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) metoduna yapılan çağrıda ana bilgisayar tarafından belirtilen bir değer olabilir.  
  
 Tüm ilke eylemi değerleri CLR işlemleri için zaman aşımı davranışı olarak belirtilemez. `SetActionOnTimeout` genellikle davranışı yükseltmek için kullanılır. Örneğin, bir ana bilgisayar, iş parçacığı iptal işlemini işlenmemiş iş parçacığı iptal edilecek olarak belirtebilir, ancak tersini belirtemez. Aşağıdaki tabloda `action` geçerli değerler için geçerli değerler açıklanmaktadır `operation` .  
  
|Değer `operation`|İçin geçerli değerler `action`|  
|---------------------------|-------------------------------|  
|OPR_ThreadRudeAbortInNonCriticalRegion<br /><br /> OPR_ThreadRudeAbortInCriticalRegion|-eRudeAbortThread<br />-eUnloadAppDomain<br />-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_AppDomainUnload|-eUnloadAppDomain<br />-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_ProcessExit|-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrOperation Numaralandırması](eclroperation-enumeration.md)
- [EPolicyAction Numaralandırması](epolicyaction-enumeration.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
