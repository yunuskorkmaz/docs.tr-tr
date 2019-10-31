---
title: ICLRMetaHostPolicy::GetRequestedRuntime Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 1b07029990ef529ded57bc569beff1061ad0f938
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140873"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime Yöntemi

Bir barındırma ilkesi, yönetilen derleme, sürüm dizesi ve yapılandırma akışı temelinde ortak dil çalışma zamanının (CLR) tercih edilen bir sürümüne arabirim sağlar. Bu yöntem, CLR 'yi gerçekten yüklemez veya etkinleştirmez, ancak ilke sonucunu temsil eden [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimini geri döndürür. Bu yöntem, [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)ve [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) yöntemlerinin yerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
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

## <a name="parameters"></a>Parametreler

|Name|Açıklama|
|----------|-----------------|
|`dwPolicyFlags`|'ndaki Gerekli. Bir bağlama ilkesini ve herhangi bir sayıda değiştiriciyi temsil eden [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) numaralandırması üyesini belirtir. Şu anda kullanılabilir olan tek ilke [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)' dir.<br /><br /> Değiştiriciler şunlardır [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)ve [METAHOST_POLICY_ ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|
|`pwzBinary`|'ndaki Seçim. Derleme dosyası yolunu belirtir.|
|`pCfgStream`|'ndaki Seçim. Yapılandırma dosyasını <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>olarak belirtir.|
|`pwzVersion`|[in, out] Seçim. Yüklenecek tercih edilen CLR sürümünü belirtir veya döndürür.|
|`pcchVersion`|[in, out] Gerekli. Arabellek taşmalarını önlemek için beklenen `pwzVersion` boyutunu giriş olarak belirtir. `pwzVersion` null ise, `pcchVersion`, ön ayırmaya izin vermek için `GetRequestedRuntime` döndüğünde beklenen `pwzVersion` boyutunu içerir; Aksi takdirde, `pcchVersion` `pwzVersion`yazılan karakter sayısını içerir.|
|`pwzImageVersion`|dışı Seçim. `GetRequestedRuntime` döndüğünde, döndürülen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimine KARŞıLıK gelen CLR sürümünü içerir.|
|`pcchImageVersion`|[in, out] Seçim. Arabellek taşmalarını önlemek için `pwzImageVersion`, giriş olarak boyutunu belirtir. `pwzImageVersion` null ise, `pcchImageVersion`, ön ayırmaya izin vermek için `GetRequestedRuntime` döndüğünde `pwzImageVersion` gereken boyutunu içerir.|
|`pdwConfigFlags`|dışı Seçim. `GetRequestedRuntime` bağlama işlemi sırasında bir yapılandırma dosyası kullanıyorsa, `pdwConfigFlags`, [\<startup >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) öğesinin `useLegacyV2RuntimeActivationPolicy` özniteliği kümesine sahip olup olmadığını belirten bir [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) değeri içerir ve değerini özniteliği. `useLegacyV2RuntimeActivationPolicy`ilgili değerleri almak için `pdwConfigFlags` için [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) maskesini uygulayın.|
|`riid`|'ndaki İstenen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi için IID_ICLRRuntimeInfo arabirim tanımlayıcısını belirtir.|
|`ppRuntime`|dışı `GetRequestedRuntime` döndüğünde, karşılık gelen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimine bir işaretçi içerir.|

## <a name="remarks"></a>Açıklamalar

Bu yöntem başarılı olduğunda, ek bayrakları, döndürülen çalışma zamanı arabiriminin geçerli varsayılan başlatma bayraklarıyla Birleştirme yan etkisi vardır ve yalnızca `<configuration><runtime>` içindeki yapılandırma akışında aşağıdaki öğelerden biri veya birkaçı varsa kısmı

- `<gcServer enabled="true"/>` `STARTUP_SERVER_GC` ayarlamaya neden olur.

- `<etwEnable enabled="true"/>` `STARTUP_ETW` ayarlamaya neden olur.

- `<appDomainResourceMonitoring enabled="true"/>` `STARTUP_ARM` ayarlamaya neden olur.

Elde edilen varsayılan `STARTUP_FLAGS` değeri, yukarıdaki listeden varsayılan başlangıç bayraklarıyla ayarlanan değerlerin bit seviyesinde veya birleşimidir.

## <a name="return-value"></a>Dönüş Değeri

Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.

|HRESULT|Açıklama|
|-------------|-----------------|
|S_OK|Yöntem başarıyla tamamlandı.|
|E_POINTER|`pwzVersion` null değil ve `pcchVersion` null.<br /><br /> veya<br /><br /> `pwzImageVersion` null değil ve `pcchImageVersion` null.|
|E_INVALIDARG|`dwPolicyFlags` `METAHOST_POLICY_HIGHCOMPAT`belirtmiyor.|
|ERROR_INSUFFICIENT_BUFFER|`pwzVersion` için ayrılan bellek yetersiz.<br /><br /> veya<br /><br /> `pwzImageVersion` için ayrılan bellek yetersiz.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags`, METAHOST_POLICY_APPLY_UPGRADE_POLICY içerir ve hem `pwzVersion` hem de `pcchVersion` null.|

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** MetaHost. h

**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir

**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHostPolicy Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
