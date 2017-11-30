---
title: "GetRequestedRuntimeVersionForCLSID İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersionForCLSID
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersionForCLSID
helpviewer_keywords: GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a5b9e4b186b6c9b91c1182e8700268f0e1c038f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID İşlevi
Belirtilen sınıfı için uygun ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır `CLSID`.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `rclsid`  
 [in]  `CLSID` Bileşeninin.  
  
 `pVersion`  
 [out]  Başarıyla tamamlandıktan sonra sürüm numarası dizesi içeren bir arabellek.  
  
 `cchBuffer`  
 [in]  Geniş karakterler boyutu, `pVersion` arabellek.  
  
 `dwLength`  
 [out] Bayt cinsinden döndürülen arabellek uzunluğu.  
  
 `dwResolutionFlags`  
 [in]  Clsıd_resolutıon_flags değerlerinden biri. Aşağıdaki değerleri desteklenir:  
  
-   CLSID_RESOLUTION_DEFAULT: Bu varsayılan birlikte çalışma davranışı belirtir (0x0) olmalıdır kullanılır.  
  
-   CLSID_RESOLUTION_REGISTERED: kayıt defteri aranıp aranmayacağını ve dolguya ilkesi belirtir (0x1) olmalıdır uygulanır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İşlev başarıyla döndürüldü.|  
|E_INVALIDARG|Parametrelerden biri geçersiz tür veya biçimi vardır.|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion` Arabelleği tüm sürüm dizesi tutmak için yeterince büyük değil.|  
|REGDB_E_CLASSNOTREG|Belirtilen ile kayıtlı bir sınıf yok `CLSID`.|  
|E_POINTER|`dwLength`null, veya `cchBuffer` sürüm dizesi tutmak için yeterince büyük olduğundan, ancak `pVersion` null.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
