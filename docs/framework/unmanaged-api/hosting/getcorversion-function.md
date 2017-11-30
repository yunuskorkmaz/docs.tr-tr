---
title: "GetCORVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORVersion
helpviewer_keywords: GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6218714030892531f3b9ed4b4a79917347d250db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
