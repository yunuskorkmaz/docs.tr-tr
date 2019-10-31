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
ms.openlocfilehash: 1283abaf6b08af1d842d8fe4469f7f6c15e38ec5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136430"
---
# <a name="getcorversion-function"></a>GetCORVersion İşlevi
Geçerli işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını döndürür.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
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
 CLR 'nin şu anda işleme yüklenmiş çalışma zamanının sürümünü belirten bir dize döndürdüğü bir arabelleğin işaretçisi. Döndürülen dize [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)öğesine geçirilen dizelerle aynı formu alır, örneğin, "v 1.0.1216". Çalışma zamanı işleme henüz yüklenmemişse, işlev, bilgisayarda yüklü olan çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.  
  
 `cchBuffer`  
 `pbuffer`tutulabilecek karakter sayısı (`WCHAR`s).  
  
 `dwLength`  
 `pbuffer`' de aslında döndürülen karakter sayısına yönelik bir işaretçi. `pbuffer` null işaretçisiyse, çalışma zamanı E_POINTER döndürür. Karakter sayısı daha büyükse `pbuffer`, çalışma zamanı ERROR_INSUFFICIENT_BUFFER döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
