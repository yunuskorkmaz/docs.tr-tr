---
title: IValidator::FormatEventInfo Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 875052ed26e83de50807e33e9c74dcf89f7ee679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440651"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
