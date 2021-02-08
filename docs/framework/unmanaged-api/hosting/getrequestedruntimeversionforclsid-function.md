---
description: ': GetRequestedRuntimeVersionForCLSID Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 10fdc947181d3f1fa12b33f11cf31b68fc4285cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785269"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID İşlevi

Belirtilen sınıf için uygun ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır `CLSID` .  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
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
 'ndaki  `CLSID` Bileşen.  
  
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
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|İşlev başarıyla döndürüldü.|  
|E_INVALIDARG|Parametrelerden birinde geçersiz bir tür veya biçim vardır.|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`Arabellek, tüm sürüm dizesini tutabilecek kadar büyük değil.|  
|REGDB_E_CLASSNOTREG|Belirtilen ile kayıtlı bir sınıf yok `CLSID` .|  
|E_POINTER|`dwLength` null veya `cchBuffer` Sürüm dizesini tutabilecek kadar büyük, ancak `pVersion` null.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
