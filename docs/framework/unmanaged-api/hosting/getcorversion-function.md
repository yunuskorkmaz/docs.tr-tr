---
title: GetCORVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0e922273a7d4e5b98c1321992e5e89e01adb437
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431499"
---
# <a name="getcorversion-function"></a>GetCORVersion İşlevi
Geçerli işlemde çalışan ortak dil çalışma zamanı (CLR) sürüm numarasını döndürür.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbuffer`  
 Bir işaretçi bir arabellek için CLR işlemine yüklü çalışma zamanı sürümü belirten bir dize döndürür. Dizeleri geçirilecek şekilde döndürülen dize aynı biçimdedir [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), örneğin, "v1.0.1216". Çalışma zamanı işlemine henüz yüklenmedi, işlevi bilgisayarda yüklü çalışma zamanı en son sürümü için uygun dizin bilgileri döndürür.  
  
 `cchBuffer`  
 Karakter sayısı (`WCHAR`s), tutulan içinde `pbuffer`.  
  
 `dwLength`  
 Gerçekte döndürülen karakter sayısını gösteren bir işaretçi `pbuffer`. Varsa `pbuffer` null işaretçi, çalışma zamanı E_POINTER döndürür. Karakter sayısını büyükse, ardından uzunluğu `pbuffer` , çalışma zamanı ERROR_INSUFFICIENT_BUFFER döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
