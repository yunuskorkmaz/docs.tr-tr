---
title: "CorBindToRuntimeByCfg İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeByCfg
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeByCfg
helpviewer_keywords: CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dccd777ef20f68d091cfdd7939c57a1f8d42ad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg İşlevi
Ortak dil çalışma zamanı (CLR), bir XML dosyasından okuma sürüm bilgilerini kullanarak bir sürecine yükler.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pCfgStream`  
 [in] Bir işaretçi bir `IStream` XML dosyasını okur nesnesi.  
  
 `reserved`  
 [in] Gelecekte kullanılmak üzere ayrılmış. 0 (sıfır) değeri olarak kullanın.  
  
 `startupFlags`  
 [in] Değerini [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) CLR başlatma davranışını belirtir numaralandırması.  
  
 `rclsid`  
 [in] `CLSID` Ya da uygulayan coclass'ı, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi. Değerleri CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost desteklenir.  
  
 `riid`  
 [in] `IID` Herhangi birinin `ICorRuntimeHost` veya `ICLRRuntimeHost` arabirimi. Değerleri IID_ICorRuntimeHost veya IID_ICLRRuntimeHost desteklenir.  
  
 `ppv`  
 [out] Döndürülen arabiriminin adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML dosyasının formatı sonra standart uygulama yapılandırma dosyası modellenir. XML dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyası şeması](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
