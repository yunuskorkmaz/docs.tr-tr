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
ms.openlocfilehash: fe5525fc29bc01bb84f7f2997d115eec12d72b13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736278"
---
# <a name="getcorversion-function"></a>GetCORVersion İşlevi
Geçerli işlemde çalışan ortak dil çalışma zamanı (CLR) sürüm numarasını döndürür.  
  
 Bu işlev .NET Framework 4'te kullanım dışıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametreler  
 `pbuffer`  
 CLR işleme şu anda yüklü olan çalışma zamanı sürümü belirten bir dize döndüren arabellek için işaretçi. Geçirilen dizeler olarak döndürülen dizeyi aynı forma alan [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), örneğin, "v1.0.1216". Çalışma zamanı işleme henüz yüklenmemiş bir bilgisayarda yüklü olan çalışma zamanı en son sürümü için uygun dizin bilgileri işlevi döndürür.  
  
 `cchBuffer`  
 Karakter sayısı (`WCHAR`s), tutulan içinde `pbuffer`.  
  
 `dwLength`  
 Gerçekte döndürülen karakter sayısı için bir işaretçi `pbuffer`. Varsa `pbuffer` null bir işaretçiyse, çalışma zamanı e_poınter döndürür. Karakter sayısı büyükse, ardından uzunluğunu `pbuffer` , çalışma zamanı ERROR_INSUFFICIENT_BUFFER döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
