---
title: IValidator::Validate Yöntemi
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 840a3779ca5692787c2c352db60a29d6a4d4ba4f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768597"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate Yöntemi
Belirtilen taşınabilir yürütülebilir (PE) veya Microsoft Ara dili (MSIL) dosyası doğrular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `veh`  
 [in] Bir işaretçi bir `IVEHandler` doğrulama hatalarını işleyen örneği.  
  
 `pAppDomain`  
 [in] Dosya yüklendiği uygulama etki alanı için bir işaretçi.  
  
 `ulFlags`  
 [in] Bitsel bir birleşimi [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) gerçekleştirilmelidir Doğrulamalar gösteren değer.  
  
 `ulMaxError`  
 [in] Doğrulama çıkmadan önce izin vermek için hataları sayısı.  
  
 `token`  
 [in] Kullanılmıyor.  
  
 `fileName`  
 [in] Doğrulanacak dosyasının adını belirten dize.  
  
 `pe`  
 [in] Dosyanın depolandığı ara belleğe yönelik işaretçi.  
  
 `ulSize`  
 [in] Doğrulanacak dosyasının bayt cinsinden boyutu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** IValidator.idl, IValidator.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
