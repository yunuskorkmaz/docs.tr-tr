---
title: ICLRMetaHostPolicy::GetRequestedRuntime Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0501e104b2ed74656de125e668b7234efcbc9997
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime Metodu
Ortak dil çalışma zamanı (CLR) tercih edilen bir sürümünü barındırma İlkesi, yönetilen derleme, sürüm dizesi ve yapılandırma akış temel alan bir arabirim sağlar. Bu yöntem gerçekten yüklemek veya yalnızca verir ancak CLR etkinleştirme [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) İlkesi sonucu temsil eden arabirim. Bu yöntem yerini [Getrequestedruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), ve [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) yöntemleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRequestedRuntime(  
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,  
    [in]  LPCWSTR pwzBinary,  
    [in]  IStream *pCfgStream,  
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,  
    [in, out]  DWORD *pcchVersion,  
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,  
    [in, out]  DWORD *pcchImageVersion,  
    [out] DWORD *pdwConfigFlags,  
    [in]  REFIID  riid  
    [out, iid_is(riid), retval] LPVOID *ppRuntime);  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|`dwPolicyFlags`|[in] Gerekli. Üye belirtir [metahost_polıcy_flags](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) bir bağlama ilkesini ve herhangi bir sayıda değiştiricileri temsil eden numaralandırma. Şu anda kullanılabilir değil yalnızca ilke [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Değiştiriciler dahil [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), ve [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|  
|`pwzBinary`|[in] İsteğe bağlı. Derleme dosyası yolunu belirtir.|  
|`pCfgStream`|[in] İsteğe bağlı. Yapılandırma dosyası olarak belirten bir <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|  
|`pwzVersion`|[içinde out] İsteğe bağlı. Yüklenecek tercih edilen CLR sürümü döndürür veya belirtir.|  
|`pcchVersion`|[içinde out] Gerekli. Beklenen boyutunu belirtir `pwzVersion` arabellek taşmaları önlemek için giriş olarak. Varsa `pwzVersion` null, `pcchVersion` beklenen boyutu içeren `pwzVersion` zaman `GetRequestedRuntime` öncesi ayırma; Aksi takdirde olanak verir, `pcchVersion` yazılan karakter sayısını içeren `pwzVersion`.|  
|`pwzImageVersion`|[out] İsteğe bağlı. Zaman `GetRequestedRuntime` döndürür, CLR sürümü karşılık gelen içeren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) döndürüldü arabirim.|  
|`pcchImageVersion`|[içinde out] İsteğe bağlı. Boyutunu belirtir `pwzImageVersion` arabellek taşmaları önlemek için giriş olarak. Varsa `pwzImageVersion` null, `pcchImageVersion` gerekli boyutunu içeren `pwzImageVersion` zaman `GetRequestedRuntime` öncesi ayırma olanak verir.|  
|`pdwConfigFlags`|[out] İsteğe bağlı. Varsa `GetRequestedRuntime` döndüğünde, bağlama işlemi sırasında bir yapılandırma dosyasını kullanır `pdwConfigFlags` içeren bir [metahost_confıg_flags](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) gösteren değer olup olmadığını [ \<başlangıç >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) öğeye sahip `useLegacyV2RuntimeActivationPolicy` öznitelik kümesi ve özniteliğinin değeri. Uygulama [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) için maske `pdwConfigFlags` ilgili değerleri almak için `useLegacyV2RuntimeActivationPolicy`.|  
|`riid`|[in] İstenen arabirim tanımlayıcısı IID_ICLRRuntimeInfo belirtir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.|  
|`ppRuntime`|[out] Zaman `GetRequestedRuntime` döndürür, karşılık gelen bir işaretçi içeriyor [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem başarılı olduğunda içinde yapılandırma akışında bir veya daha fazla aşağıdaki öğeleri yok ve yalnızca, bu ek bayrakları geçerli varsayılan başlangıç bayrağı döndürülen çalışma zamanı arabiriminin ile birleştirme yan etkisi vardır `<configuration><runtime>` Bölüm:  
  
-   `<gcServer enabled="true"/>`neden `STARTUP_SERVER_GC` ayarlanmalıdır.  
  
-   `<etwEnable enabled="true"/>`neden `STARTUP_ETW` ayarlanmalıdır.  
  
-   `<appDomainResourceMonitoring enabled="true"/>`neden `STARTUP_ARM` ayarlanmalıdır.  
  
 Sonuçta elde edilen varsayılan `STARTUP_FLAGS` varsayılan başlangıç bayraklarla yukarıdaki listede kümeden değerlerin Bitsel veya birleşimi bir değerdir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzVersion`NULL olmayan ve `pcchVersion` null.<br /><br /> veya<br /><br /> `pwzImageVersion`NULL olmayan ve `pcchImageVersion` null.|  
|E_INVALIDARG|`dwPolicyFlags`belirtmediği `METAHOST_POLICY_HIGHCOMPAT`.|  
|ERROR_INSUFFICIENT_BUFFER|Bellek tahsis `pwzVerison` yeterli değildir.<br /><br /> veya<br /><br /> Bellek tahsis `pwzImageVerison` yeterli değildir.|  
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags`METAHOST_POLICY_APPLY_UPGRADE_POLICY ve her ikisi de içeren `pwzVersion` ve `pcchVersion` null.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRMetaHostPolicy Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
