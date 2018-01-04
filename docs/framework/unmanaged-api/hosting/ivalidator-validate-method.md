---
title: "IValidator::Validate Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a74249cb806f332b3ae575223f237438da616972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate Yöntemi
Belirtilen taşınabilir yürütülebilir (PE) ya da Microsoft Ara dili (MSIL) dosya doğrular.  
  
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
 [in] Bir işaretçi bir `IVEHandler` doğrulama hataları işleyen örneği.  
  
 `pAppDomain`  
 [in] Dosyayı yüklendiği uygulama etki alanı için bir işaretçi.  
  
 `ulFlags`  
 [in] Bit düzeyinde bileşimini [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) gerçekleştirilmelidir doğrulamaları belirten değer.  
  
 `ulMaxError`  
 [in] Doğrulama çıkmadan önce izin vermek için hatası sayısı.  
  
 `token`  
 [in] Kullanılmıyor.  
  
 `fileName`  
 [in] Doğrulanacak dosyasının adını belirten dize.  
  
 `pe`  
 [in] Dosyanın depolandığı bellek arabellek için bir işaretçi.  
  
 `ulSize`  
 [in] Doğrulanacak dosyasının bayt cinsinden boyutu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** IValidator.idl, IValidator.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
