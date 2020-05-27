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
ms.openlocfilehash: 0c60631b5e034bc46d74412440d35d526359d043
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008579"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo Yöntemi
Belirtilen doğrulama hatasına karşılık gelen hata iletisini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hVECode`  
 'ndaki Doğrulama hata işleyicisine geçirilen HRESULT değeri.  
  
 `Context`  
 'ndaki `VEContext`Doğrulama hatası hakkında bağlam bilgilerini içeren bir örnek.  
  
 `msg`  
 [in, out] Döndürülen hata iletisini içeren bir dize.  
  
 `ulMaxLength`  
 'ndaki Hata iletisinin en fazla uzunluğu.  
  
 `psa`  
 'ndaki Hatayı açıklayan ek parametreler içeren bir güvenli dizi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** IValidator. IDL, IValidator. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
