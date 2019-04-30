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
ms.openlocfilehash: 697557463aa949036acb21e63b9a82b1fb84b415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765290"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx İşlevi
HRESULT değerini belirtilen kültür için uygun hata iletisine çevirir.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
