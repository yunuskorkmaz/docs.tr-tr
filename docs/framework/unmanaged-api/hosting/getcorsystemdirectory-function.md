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
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178199"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory İşlevi
İşleme yüklenen ortak dil çalışma zamanının (CLR) yükleme dizini verir. Yükleme dizini, örneğin "c:\windows\microsoft.net\framework\v1.0.3705" gibi tam niteliklidir.  
  
 Bu işlev amortismana hazır. Bu [ICLRRuntimeInfo tarafından yerini::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) yöntemi .NET Framework 4 sağlanan.  
  
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
 [çıkış] Çalışma zamanının, işleme yüklenen çalışma zamanı için yükleme dizininin tam nitelikli adını içeren bir dize döndürdİğİ bir arabellek. Çalışma süresi henüz işleme yüklenmediyse, işlev bilgisayarda yüklenen çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.  
  
 `cchBuffer`  
 [içinde] Boyutu, bayt, ve. `pbuffer`  
  
 `dwLength`  
 [çıkış] Döndürülen karakter `pbuffer`sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!CAUTION]
> CLR'nin sürüm 4'ü çalıştıran işlemlerde bu işlevi kullanmayın. CLR'nin önceki bir sürümü bilgisayara yüklenmişse, bu işlev bu sürümün yükleme dizinini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
