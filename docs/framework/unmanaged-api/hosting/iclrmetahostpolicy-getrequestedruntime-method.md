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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73d5c98500c510630b1f8d6081b654a6dbd88a5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771807"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime Yöntemi

Tercih edilen bir ortak dil çalışma zamanı (CLR) sürümünü barındırma İlkesi, yönetilen derleme, sürüm dizesi ve yapılandırma akışı temel alan bir arabirim sağlar. Bu yöntem gerçekten yüklemek veya yalnızca döndürür ancak CLR etkinleştirme [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) İlkesi sonucu temsil eden arabirim. Bu yöntem yerine geçer [Getrequestedruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), ve [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) yöntemleri.

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

|Ad|Açıklama|
|----------|-----------------|
|`dwPolicyFlags`|[in] Gerekli. Üye belirtir [metahost_polıcy_flags](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) bağlama ilkesi ve değiştiricilere ait herhangi bir sayıyı temsil eden bir numaralandırma. Şu anda yalnızca ilke [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Değiştiriciler dahil [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), ve [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|
|`pwzBinary`|[in] İsteğe bağlı. Derleme dosya yolunu belirtir.|
|`pCfgStream`|[in] İsteğe bağlı. Yapılandırma dosyası olarak belirten bir <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|`pwzVersion`|[out içinde] İsteğe bağlı. Yüklenecek tercih edilen CLR sürümü döndürür veya belirtir.|
|`pcchVersion`|[out içinde] Gerekli. Beklenen boyutunu belirtir `pwzVersion` arabellek taşması önlemek için giriş olarak. Varsa `pwzVersion` boş `pcchVersion` beklenen boyutunu içeren `pwzVersion` olduğunda `GetRequestedRuntime` ön ayırması; Aksi takdirde olanak verir, `pcchVersion` yazılan karakter sayısını içeren `pwzVersion`.|
|`pwzImageVersion`|[out] İsteğe bağlı. Zaman `GetRequestedRuntime` döndürür, CLR sürümü için karşılık gelen içeren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) döndürülen arabirimi.|
|`pcchImageVersion`|[out içinde] İsteğe bağlı. Boyutunu belirtir `pwzImageVersion` arabellek taşması önlemek için giriş olarak. Varsa `pwzImageVersion` null, `pcchImageVersion` gerekli boyutunu içerir `pwzImageVersion` olduğunda `GetRequestedRuntime` ön ayırması izin verecek şekilde döndürür.|
|`pdwConfigFlags`|[out] İsteğe bağlı. Varsa `GetRequestedRuntime` döndüğünde, bağlama işlemi sırasında bir yapılandırma dosyası kullanır `pdwConfigFlags` içeren bir [metahost_confıg_flags](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) gösteren değer olup olmadığını [ \<başlangıç >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) öğesinin `useLegacyV2RuntimeActivationPolicy` öznitelik kümesi ve öznitelik değeri. Uygulama [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) için maske `pdwConfigFlags` ilgili değerleri almak için `useLegacyV2RuntimeActivationPolicy`.|
|`riid`|[in] İstenen için arabirim tanımlayıcısı IID_ICLRRuntimeInfo belirtir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.|
|`ppRuntime`|[out] Zaman `GetRequestedRuntime` döndürür, karşılık gelen bir işaretçi içeren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.|

## <a name="remarks"></a>Açıklamalar

Bu yöntem başarılı olduğunda yapılandırma akış içinde bir veya daha fazla aşağıdaki öğe var ve yalnızca, bu ek bayrakları geçerli varsayılan başlangıç bayrağı döndürülen çalışma zamanı arabiriminin ile birleştirme yan etkisi sahip `<configuration><runtime>` Bölüm:

- `<gcServer enabled="true"/>` neden `STARTUP_SERVER_GC` ayarlanacak.

- `<etwEnable enabled="true"/>` neden `STARTUP_ETW` ayarlanacak.

- `<appDomainResourceMonitoring enabled="true"/>` neden `STARTUP_ARM` ayarlanacak.

Sonuçta elde edilen varsayılan `STARTUP_FLAGS` değerdir önceki listede varsayılan başlangıç bayrağı ile ayarlanan değerlerle bit düzeyindeki OR kombinasyonudur.

## <a name="return-value"></a>Dönüş Değeri

Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.

|HRESULT|Açıklama|
|-------------|-----------------|
|S_OK|Yöntem başarıyla tamamlandı.|
|E_POINTER|`pwzVersion` null değil ve `pcchVersion` null.<br /><br /> -veya-<br /><br /> `pwzImageVersion` null değil ve `pcchImageVersion` null.|
|E_INVALIDARG|`dwPolicyFlags` belirttiğinde `METAHOST_POLICY_HIGHCOMPAT`.|
|ERROR_INSUFFICIENT_BUFFER|Bellek tahsis `pwzVersion` yeterli değildir.<br /><br /> -veya-<br /><br /> Bellek tahsis `pwzImageVersion` yeterli değildir.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` METAHOST_POLICY_APPLY_UPGRADE_POLICY ve her ikisi de içeren `pwzVersion` ve `pcchVersion` null.|

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** MetaHost.h

**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil

**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHostPolicy Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
