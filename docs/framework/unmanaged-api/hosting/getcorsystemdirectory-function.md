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
ms.openlocfilehash: 137b2e30916cb1934d4389c5668bfb7eb5066064
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617236"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory İşlevi
İşleme yüklenen ortak dil çalışma zamanının (CLR) yükleme dizinini döndürür. Yükleme dizini tam olarak nitelenir, örneğin "c:\Windows\Microsoft.NET\Framework\v1.0.3705".  
  
 Bu işlev kullanım dışıdır. .NET Framework 4 ' te belirtilen [ICLRRuntimeInfo:: GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) yöntemi ile değiştirilmiştir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Bayt cinsinden boyutu `pbuffer` .  
  
 `dwLength`  
 dışı İçinde döndürülen karakterlerin sayısı `pbuffer` .  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!CAUTION]
> Bu işlevi CLR sürüm 4 ' ü çalıştıran işlemlerde kullanmayın. Bilgisayarda CLR 'nin önceki bir sürümü yüklüyse, bu işlev söz konusu sürümün yükleme dizinini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
