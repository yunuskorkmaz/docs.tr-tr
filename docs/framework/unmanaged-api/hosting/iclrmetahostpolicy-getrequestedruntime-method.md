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
ms.openlocfilehash: 37167b7a9aefa6cd9d5e4df043e8bbc1b0514261
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504127"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime Yöntemi

Bir barındırma ilkesi, yönetilen derleme, sürüm dizesi ve yapılandırma akışı temelinde ortak dil çalışma zamanının (CLR) tercih edilen bir sürümüne arabirim sağlar. Bu yöntem, CLR 'yi gerçekten yüklemez veya etkinleştirmez, ancak ilke sonucunu temsil eden [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimini geri döndürür. Bu yöntem, [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)ve [GetCORRequiredVersion](getcorrequiredversion-function.md) yöntemlerinin yerini alır.

## <a name="syntax"></a>Söz dizimi

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

|Name|Description|
|----------|-----------------|
|`dwPolicyFlags`|'ndaki Gerekli. Bir bağlama ilkesini ve herhangi bir sayıda değiştiriciyi temsil eden [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) numaralandırması üyesini belirtir. Şu anda kullanılabilir olan tek ilke [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).<br /><br /> Değiştiriciler [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)ve [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md)içerir.|
|`pwzBinary`|'ndaki Seçim. Derleme dosyası yolunu belirtir.|
|`pCfgStream`|'ndaki Seçim. Yapılandırma dosyasını bir olarak belirtir <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> .|
|`pwzVersion`|[in, out] Seçim. Yüklenecek tercih edilen CLR sürümünü belirtir veya döndürür.|
|`pcchVersion`|[in, out] Gerekli. `pwzVersion`Arabellek taşmalarını önlemek için, giriş olarak beklenen boyutu belirtir. `pwzVersion`Null ise, `pcchVersion` `pwzVersion` `GetRequestedRuntime` ön ayırmaya izin vermek için, geri dönüşün beklenen boyutunu içerir; Aksi takdirde, `pcchVersion` üzerine yazılan karakter sayısını içerir `pwzVersion` .|
|`pwzImageVersion`|dışı Seçim. `GetRequestedRuntime`Döndüğünde, döndürülen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) ARABIRIMINE karşılık gelen CLR sürümünü içerir.|
|`pcchImageVersion`|[in, out] Seçim. `pwzImageVersion`Arabellek taşmalarını önlemek için giriş olarak boyutu belirtir. `pwzImageVersion`Null ise, `pcchImageVersion` `pwzImageVersion` `GetRequestedRuntime` ön ayırmaya izin vermek için, geri dönüşün gereken boyutunu içerir.|
|`pdwConfigFlags`|dışı Seçim. `GetRequestedRuntime`Bağlama işlemi sırasında bir yapılandırma dosyası kullanıyorsa, bu, öğesini döndürdüğünde, `pdwConfigFlags` öğesinde öznitelik ayarlanmış olup olmadığını belirten bir [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) değeri [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) `useLegacyV2RuntimeActivationPolicy` ve özniteliği değeri içerir. İle [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) `pdwConfigFlags` ilgili değerleri almak için METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK maskesini uygulayın `useLegacyV2RuntimeActivationPolicy` .|
|`riid`|'ndaki İstenen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi için IID_ICLRRuntimeInfo arabirim tanımlayıcısını belirtir.|
|`ppRuntime`|dışı `GetRequestedRuntime`Döndüğünde, karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine bir işaretçi içerir.|

## <a name="remarks"></a>Açıklamalar

Bu yöntem başarılı olduğunda, ek bayrakları, döndürülen çalışma zamanı arabiriminin geçerli varsayılan başlatma bayraklarıyla birleştirmenin yan etkisi vardır ve yalnızca, bölüm içindeki yapılandırma akışında aşağıdaki öğelerden biri veya birkaçı varsa `<configuration><runtime>` :

- `<gcServer enabled="true"/>``STARTUP_SERVER_GC`ayarlanmasının nedeni.

- `<etwEnable enabled="true"/>``STARTUP_ETW`ayarlanmasının nedeni.

- `<appDomainResourceMonitoring enabled="true"/>``STARTUP_ARM`ayarlanmasının nedeni.

Elde edilen varsayılan `STARTUP_FLAGS` değer, yukarıdaki listeden varsayılan başlangıç bayraklarıyla ayarlanan değerlerin bit SEVIYESINDE veya birleşimidir.

## <a name="return-value"></a>Dönüş Değeri

Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.

|HRESULT|Description|
|-------------|-----------------|
|S_OK|Yöntem başarıyla tamamlandı.|
|E_POINTER|`pwzVersion`null değil ve `pcchVersion` null.<br /><br /> -veya-<br /><br /> `pwzImageVersion`null değil ve `pcchImageVersion` null.|
|E_INVALIDARG|`dwPolicyFlags`belirtmiyor `METAHOST_POLICY_HIGHCOMPAT` .|
|ERROR_INSUFFICIENT_BUFFER|Ayrılan bellek `pwzVersion` yetersiz.<br /><br /> -veya-<br /><br /> Ayrılan bellek `pwzImageVersion` yetersiz.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags`METAHOST_POLICY_APPLY_UPGRADE_POLICY içerir ve her ikisi `pwzVersion` de `pcchVersion` null.|

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** MetaHost. h

**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir

**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHostPolicy Arabirimi](iclrmetahostpolicy-interface.md)
- [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
