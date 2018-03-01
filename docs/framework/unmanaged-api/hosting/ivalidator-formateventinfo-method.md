---
title: "IValidator::FormatEventInfo Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ddff0a640f37133bf5a44aea1e371d73d0fd2856
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo Yöntemi
Belirtilen doğrulama hatası karşılık gelen hata iletisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hVECode`  
 [in] Doğrulama hata işleyicisine geçirilen HRESULT değeri.  
  
 `Context`  
 [in] A `VEContext` doğrulama hatası hakkında bağlam bilgisi içeren örneği.  
  
 `msg`  
 [içinde out] Döndürülen hata iletisi içeren bir dize.  
  
 `ulMaxLength`  
 [in] Hata iletisinin en büyük uzunluğu.  
  
 `psa`  
 [in] Hatayı açıklayan ek parametreleri içeren güvenli bir dizi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** IValidator.idl, IValidator.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
