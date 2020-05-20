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
ms.openlocfilehash: 899d6e74902e47f1f41b849bd5c25048baa175f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617145"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID İşlevi
Belirtilen sınıf için uygun ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır `CLSID` .  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki  `CLSID`Bileşen.  
  
 `pVersion`  
 dışı  Başarılı bir şekilde tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.  
  
 `cchBuffer`  
 'ndaki  Arabelleğin geniş karakterdeki boyutu `pVersion` .  
  
 `dwLength`  
 dışı Döndürülen arabelleğin bayt cinsinden uzunluğu.  
  
 `dwResolutionFlags`  
 'ndaki  CLSID_RESOLUTION_FLAGS değerlerinden biri. Aşağıdaki değerler desteklenir:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) varsayılan birlikte çalışma davranışının kullanılması gerektiğini belirtir.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) kayıt defterinin aranması gerektiğini ve dolgu ilkesinin uygulanacağını belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlev başarıyla döndürüldü.|  
|E_INVALIDARG|Parametrelerden birinde geçersiz bir tür veya biçim vardır.|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`Arabellek, tüm sürüm dizesini tutabilecek kadar büyük değil.|  
|REGDB_E_CLASSNOTREG|Belirtilen ile kayıtlı bir sınıf yok `CLSID` .|  
|E_POINTER|`dwLength`null veya `cchBuffer` Sürüm dizesini tutabilecek kadar büyük, ancak `pVersion` null.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
