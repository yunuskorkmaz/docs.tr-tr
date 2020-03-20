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
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178111"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID İşlevi
Belirtilen `CLSID`sınıf için uygun ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 [içinde]  Bileşenin. `CLSID`  
  
 `pVersion`  
 [çıkış]  Başarılı bir şekilde tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.  
  
 `cchBuffer`  
 [içinde]  Geniş karakterlerdeki arabelleğin `pVersion` boyutu.  
  
 `dwLength`  
 [çıkış] Döndürülen arabelleğe baytlar halindeki uzunluğu.  
  
 `dwResolutionFlags`  
 [içinde]  CLSID_RESOLUTION_FLAGS değerlerinden biri. Aşağıdaki değerler desteklenir:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) Varsayılan interop davranışının kullanılması gerektiğini belirtir.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) Kayıt defterinin aranması ve şim ilkesinin uygulanması gerektiğini belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlev başarıyla döndü.|  
|E_ınvalıdarg|Parametrelerden birinin geçersiz türü veya biçimi vardır.|  
|ERROR_INSUFFICIENT_BUFFER|Arabellek `pVersion` tüm sürüm dizesini tutacak kadar büyük değil.|  
|REGDB_E_CLASSNOTREG|Belirtilen `CLSID`sınıfa kayıtlı bir sınıf yok.|  
|E_POINTER|`dwLength`null veya `cchBuffer` sürüm dizesini tutmak için `pVersion` yeterince büyük, ancak null.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
