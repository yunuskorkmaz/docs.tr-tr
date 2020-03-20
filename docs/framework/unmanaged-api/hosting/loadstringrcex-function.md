---
title: LoadStringRCEx İşlevi
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177976"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx İşlevi
HRESULT değerini belirtilen kültür için uygun bir hata iletisine çevirir.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `lcid`  
 [içinde] Bir kültür tanımlayıcısı. Varsayılan kültürü `lcid` kullanmak için -1'i geç.  
  
 `iResourceID`  
 [içinde] Bir HRESULT.  
  
 `szBuffer`  
 [çıkış] Başarılı bir şekilde tamamlandıktan sonra hata iletisi içeren bir arabellek.  
  
 `iMax`  
 [içinde] Hata iletisi arabelleği boyutu.  
  
 `bQuiet`  
 [içinde] Göz ardı.  
  
 `pcwchUsed`  
 [çıkış] Hata iletisinin uzunluğuna işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_ınvalıdarg|`szBuffer`null veya `iMax` sıfır (0) ise.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem başarıyla tamamlanmamışsa, `szBuffer` boş bir dize içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC İşlevi](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
