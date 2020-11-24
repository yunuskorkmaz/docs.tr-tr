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
ms.openlocfilehash: 4ce50f7706583f291d2e6a141d40ab6dd3e4b3e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674391"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate Yöntemi

Belirtilen dosyadaki taşınabilir yürütülebilir (PE) veya Microsoft ara dili 'ni (MSIL) doğrular.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `IVEHandler` Doğrulama hatalarını işleyen bir örneğe yönelik işaretçi.  
  
 `ulAppDomainId`  
 'ndaki Geçerli için tanımlayıcı <xref:System.AppDomain> .  
  
 `ulFlags`  
 'ndaki Gerçekleştirilmesi gereken doğrulamanın türünü belirten [ValidatorFlags](validatorflags-enumeration.md) değerlerinin birleşimi.  
  
 `ulMaxError`  
 'ndaki Doğrulamadan çıkmadan önce izin verilen en fazla hata sayısı.  
  
 `token`  
 'ndaki Kullanılmayan.  
  
 `fileName`  
 'ndaki Doğrulanacak dosyanın adı.  
  
 `pe`  
 'ndaki Dosya arabelleği işaretçisi.  
  
 `ulSize`  
 'ndaki Doğrulanacak dosyanın bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Validate` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** IValidator. IDL, IValidator. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRValidator Arabirimi](iclrvalidator-interface.md)
