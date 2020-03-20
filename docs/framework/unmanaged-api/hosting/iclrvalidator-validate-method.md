---
title: ICLRValidator::Validate Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178058"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate Yöntemi
Belirtilen dosyadaki taşınabilir yürütülebilir (PE) veya Microsoft ara dilini (MSIL) doğrular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a>Parametreler  
 `veh`  
 [içinde] Doğrulama hatalarını `IVEHandler` işleyen bir örneğin işaretçisi.  
  
 `ulAppDomainId`  
 [içinde] Geçerli <xref:System.AppDomain>için tanımlayıcı .  
  
 `ulFlags`  
 [içinde] Yapılması gereken doğrulama türünü gösteren [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) değerlerinin birleşimi.  
  
 `ulMaxError`  
 [içinde] Doğrulamadan çıkmadan önce izin verilebilen maksimum hata sayısı.  
  
 `token`  
 [içinde] Kullanılma -yan.  
  
 `fileName`  
 [içinde] Doğrulanacak dosyanın adı.  
  
 `pe`  
 [içinde] Dosya arabelleği için bir işaretçi.  
  
 `ulSize`  
 [içinde] Doğrulanacak dosyanın boyutu, baytlar halinde.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Validate`başarıyla döndürülür.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** IValidator.idl, IValidator.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRValidator Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
