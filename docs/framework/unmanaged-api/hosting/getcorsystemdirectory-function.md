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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a412bd8410750ec826762e45d70d59c514c61542
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490376"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory İşlevi
İşlem içine yüklenmiş ortak dil çalışma zamanının (CLR) yükleme dizinini döndürür. Yükleme dizini tam, örneğin, "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Bu işlev kullanım dışı bırakılmıştır. Yerine geçen [Iclrruntimeınfo::getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) .NET Framework 4'te sağlanan yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametreler  
 `pbuffer`  
 [out] Çalışma zamanı yükleme dizini işleme yüklenecek çalışma zamanı için tam adını içeren bir dize döndüren bir arabellek. Çalışma zamanı işleme henüz yüklenmemiş bir bilgisayarda yüklü olan çalışma zamanı en son sürümü için uygun dizin bilgileri işlevi döndürür.  
  
 `cchBuffer`  
 [in] Bayt cinsinden boyutu, `pbuffer`.  
  
 `dwLength`  
 [out] Döndürülen karakter sayısını `pbuffer`.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!CAUTION]
>  Bu işlev, CLR sürüm 4 çalıştıran işlemlerinde kullanmayın. Bu işlev, CLR'nin önceki bir sürümü bilgisayarda yüklüyse, bu sürüm için yükleme dizinini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
