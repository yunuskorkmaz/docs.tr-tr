---
title: ICLRPolicyManager::SetActionOnFailure Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504114"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure Yöntemi
Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `failure`  
 'ndaki İşlem gerçekleştirilecek hata türünü belirten [EClrFailure](eclrfailure-enumeration.md) değerlerinden biri.  
  
 `action`  
 'ndaki Bir hata oluştuğunda gerçekleştirilecek eylemi belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri. Desteklenen değerlerin bir listesi için, açıklamalar bölümüne bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|Belirtilen işlem için bir ilke eylemi ayarlanamaz veya işlem için geçersiz bir ilke eylemi belirtildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, CLR bellek gibi bir kaynağı ayıramadığında bir özel durum oluşturur. `SetActionOnFailure`konağın hata sonrasında gerçekleştirilecek ilke eylemini belirterek bu davranışı geçersiz kılmasına izin verir. Aşağıdaki tabloda, desteklenen [EClrFailure](eclrfailure-enumeration.md) ve [EPolicyAction](epolicyaction-enumeration.md) değerlerinin birleşimleri gösterilmektedir. (FAIL_ ön eki [EClrFailure](eclrfailure-enumeration.md) değerlerinden çıkarılır.)  
  
||CriticalHandle dışı kaynak|Kritikkaynak|FatalRuntime|OrphanedLock|StackOverflow|Accessihlaihlaline|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|X|X||||Yok||  
|eThrowException|X|X||||Yok||  
|`eAbortThread`|X|X||||Yok|X|  
|`eRudeAbortThread`|X|X||||Yok|X|  
|`eUnloadAppDomain`|X|X||X||Yok|X|  
|`eRudeUnloadAppDomain`|X|X||X|X|Yok|X|  
|`eExitProcess`|X|X||X|X|Yok|X|  
|eFastExitProcess|X|X||X|X|Yok||  
|`eRudeExitProcess`|X|X|X|X|X|Yok||  
|`eDisableRuntime`|X|X|X|X|X|Yok||  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](eclrfailure-enumeration.md)
- [EPolicyAction Sabit Listesi](epolicyaction-enumeration.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
