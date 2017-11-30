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
ms.openlocfilehash: bbf5a486246d1fb596c08f1510e6d5d89b03df62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [CorBindToCurrentRuntime işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeEx işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [Icorruntimehost arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
