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
ms.openlocfilehash: 03a8bf7e215794f4a2951fe4e2d54a791bda20e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594063"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate Yöntemi
Belirtilen taşınabilir yürütülebilir (PE) veya Microsoft Ara dili (MSIL) dosyası doğrular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
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
  
## <a name="see-also"></a>Ayrıca bkz.

