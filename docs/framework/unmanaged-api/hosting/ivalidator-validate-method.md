---
description: ': IValidator:: Validate yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 6df70274a788b949686fe2509b525c5a8b04089c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680024"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate Yöntemi

Belirtilen Taşınabilir çalıştırılabilir (PE) veya Microsoft ara dili (MSIL) dosyasını doğrular.  
  
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
 'ndaki `IVEHandler` Doğrulama hatalarını işleyen bir örneğe yönelik işaretçi.  
  
 `pAppDomain`  
 'ndaki Dosyanın yüklendiği uygulama etki alanına yönelik bir işaretçi.  
  
 `ulFlags`  
 'ndaki Gerçekleştirilmesi gereken doğrulamaları belirten, [ValidatorFlags](validatorflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
 `ulMaxError`  
 'ndaki Doğrulamadan çıkmadan önce izin verilen en fazla hata sayısı.  
  
 `token`  
 'ndaki Kullanılmıyor.  
  
 `fileName`  
 'ndaki Doğrulanacak dosyanın adını belirten bir dize.  
  
 `pe`  
 'ndaki Dosyanın depolandığı bellek arabelleğine yönelik bir işaretçi.  
  
 `ulSize`  
 'ndaki Doğrulanacak dosyanın bayt cinsinden boyutu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** IValidator. IDL, IValidator. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
