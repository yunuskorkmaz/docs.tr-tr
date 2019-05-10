---
title: GetRequestedRuntimeVersionForCLSID İşlevi
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7a6b73006b6842032ae90c2c7a8433f5b58d175
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665049"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID İşlevi
Belirtilen sınıf için uygun ortak dil çalışma zamanı (CLR) sürümü bilgisini alır `CLSID`.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `rclsid`  
 [in]  `CLSID` Bileşen.  
  
 `pVersion`  
 [out]  Başarıyla tamamlandıktan sonra sürüm numarası dizesi içeren bir arabelleği.  
  
 `cchBuffer`  
 [in]  Geniş karakter cinsinden boyutu, `pVersion` arabellek.  
  
 `dwLength`  
 [out] Bayt cinsinden döndürülen arabellek uzunluğu.  
  
 `dwResolutionFlags`  
 [in]  Clsıd_resolutıon_flags değerlerinden biri. Aşağıdaki değerleri desteklenir:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) birlikte çalışma davranışı kullanılması gerektiğini belirtir.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) dolgu ilke uygulanabilir ve kayıt defteri aranıp aranmayacağını belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlev başarıyla döndürüldü.|  
|E_INVALIDARG|Parametrelerden biri, bir türü geçersiz veya biçim vardır.|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion` Arabelleği tüm sürüm dizesini tutabilecek kadar büyük değil.|  
|REGDB_E_CLASSNOTREG|Belirtilen ile kayıtlı bir sınıf yok `CLSID`.|  
|E_POINTER|`dwLength` null ise veya `cchBuffer` sürüm dizesi tutabilecek kadar büyük olduğunu ancak `pVersion` null.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
