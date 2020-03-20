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
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178185"
---
# <a name="getcorversion-function"></a>GetCORVersion İşlevi
Geçerli işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını verir.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
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
 CLR'nin şu anda işleme yüklenen çalışma zamanının sürümünü belirten bir dize döndürdeği arabelleği için bir işaretçi. Döndürülen dize, [CorBindToRuntimeEx'e](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)geçen dizeleri ile aynı şekilde alır, örneğin, "v1.0.1216". Çalışma süresi henüz işleme yüklenmediyse, işlev bilgisayarda yüklenen çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.  
  
 `cchBuffer`  
 'de `pbuffer`tutulabilen`WCHAR`karakter (ler) sayısı.  
  
 `dwLength`  
 Gerçekte döndürülen `pbuffer`karakter sayısına işaretçi Null `pbuffer` işaretçiise, çalışma süresi E_POINTER döndürür. Karakter sayısı daha büyükse, `pbuffer` çalışma süresi ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
