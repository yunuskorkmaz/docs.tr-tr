---
title: GetCORSystemDirectory İşlevi
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 63fb505a92683fda21b6e71a6ca891ca35afba1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136407"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory İşlevi
İşleme yüklenen ortak dil çalışma zamanının (CLR) yükleme dizinini döndürür. Yükleme dizini tam olarak nitelenir, örneğin "c:\Windows\Microsoft.NET\Framework\v1.0.3705".  
  
 Bu işlev kullanım dışıdır. .NET Framework 4 ' te belirtilen [ICLRRuntimeInfo:: GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) yöntemi ile değiştirilmiştir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametreler  
 `pbuffer`  
 dışı Çalışma zamanının, işleme yüklenmiş çalışma zamanı için yükleme dizininin tam adını içeren bir dize döndürdüğü bir arabellek. Çalışma zamanı işleme henüz yüklenmemişse, işlev, bilgisayarda yüklü olan çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.  
  
 `cchBuffer`  
 'ndaki `pbuffer`bayt cinsinden boyutu.  
  
 `dwLength`  
 dışı `pbuffer`döndürülen karakterlerin sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!CAUTION]
> Bu işlevi CLR sürüm 4 ' ü çalıştıran işlemlerde kullanmayın. Bilgisayarda CLR 'nin önceki bir sürümü yüklüyse, bu işlev söz konusu sürümün yükleme dizinini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
