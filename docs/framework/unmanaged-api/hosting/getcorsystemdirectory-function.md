---
title: "GetCORSystemDirectory İşlevi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02b695ac7f75dd38da8cd06e1444af4ae425ebd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory İşlevi
Yükleme dizini işlemine yüklenen ortak dil çalışma zamanı (CLR) döndürür. Yükleme dizini tam, örneğin, "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Bu işlev kullanım dışıdır. Yerine geçen [Iclrruntimeınfo::getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) sağlanan yöntemi [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbuffer`  
 [out] Arabellek çalışma zamanı yükleme dizini işlem içine yüklenmiş çalışma zamanı için tam adı içeren bir dize döndürür. Çalışma zamanı işlemine henüz yüklenmedi, işlevi bilgisayarda yüklü çalışma zamanı en son sürümü için uygun dizin bilgileri döndürür.  
  
 `cchBuffer`  
 [in] Bayt olarak boyutu, `pbuffer`.  
  
 `dwLength`  
 [out] Döndürülen karakter sayısını `pbuffer`.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!CAUTION]
>  Bu işlev, CLR sürüm 4 çalışan işlemleri içinde kullanmayın. CLR önceki bir sürümü bilgisayarda yüklüyse, bu işlev bu sürüm için yükleme dizinini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
