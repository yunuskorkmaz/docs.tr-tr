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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a0cac77d7bf7611acf6042298bfe6814d8f4352
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768445"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx İşlevi
HRESULT değerini belirtilen kültür için uygun hata iletisine çevirir.  
  
 Bu işlev .NET Framework 4'te kullanım dışıdır.  
  
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
 [in] Bir kültür tanımlayıcısı. -1 geçirmek `lcid` varsayılan kültür kullanılacak.  
  
 `iResourceID`  
 [in] HRESULT.  
  
 `szBuffer`  
 [out] Başarılı tamamlandığında hata iletisini içeren bir arabelleği.  
  
 `iMax`  
 [in] Hata iletisi arabellek boyutu.  
  
 `bQuiet`  
 [in] Yoksayıldı.  
  
 `pcwchUsed`  
 [out] Hata iletisi uzunluğu bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`szBuffer` null ise veya `iMax` sıfır (0).|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi başarıyla tamamlanmazsa `szBuffer` boş bir dize içeriyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC İşlevi](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
