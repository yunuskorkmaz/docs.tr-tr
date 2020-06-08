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
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="28090-102">ICLRMetaHostPolicy::GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28090-102">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="28090-103">Bir barındırma ilkesi, yönetilen derleme, sürüm dizesi ve yapılandırma akışı temelinde ortak dil çalışma zamanının (CLR) tercih edilen bir sürümüne arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="28090-103">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="28090-104">Bu yöntem, CLR 'yi gerçekten yüklemez veya etkinleştirmez, ancak ilke sonucunu temsil eden [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimini geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="28090-104">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="28090-105">Bu yöntem, [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)ve [GetCORRequiredVersion](getcorrequiredversion-function.md) yöntemlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="28090-105">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="28090-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="28090-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="28090-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28090-107">Parameters</span></span>

|<span data-ttu-id="28090-108">Name</span><span class="sxs-lookup"><span data-stu-id="28090-108">Name</span></span>|<span data-ttu-id="28090-109">Description</span><span class="sxs-lookup"><span data-stu-id="28090-109">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="28090-110">'ndaki Gerekli.</span><span class="sxs-lookup"><span data-stu-id="28090-110">[in] Required.</span></span> <span data-ttu-id="28090-111">Bir bağlama ilkesini ve herhangi bir sayıda değiştiriciyi temsil eden [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) numaralandırması üyesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="28090-111">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="28090-112">Şu anda kullanılabilir olan tek ilke [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="28090-112">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="28090-113">Değiştiriciler [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)ve [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="28090-113">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="28090-114">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="28090-114">[in] Optional.</span></span> <span data-ttu-id="28090-115">Derleme dosyası yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="28090-115">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="28090-116">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="28090-116">[in] Optional.</span></span> <span data-ttu-id="28090-117">Yapılandırma dosyasını bir olarak belirtir <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="28090-117">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="28090-118">[in, out] Seçim.</span><span class="sxs-lookup"><span data-stu-id="28090-118">[in, out] Optional.</span></span> <span data-ttu-id="28090-119">Yüklenecek tercih edilen CLR sürümünü belirtir veya döndürür.</span><span class="sxs-lookup"><span data-stu-id="28090-119">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="28090-120">[in, out] Gerekli.</span><span class="sxs-lookup"><span data-stu-id="28090-120">[in, out] Required.</span></span> <span data-ttu-id="28090-121">`pwzVersion`Arabellek taşmalarını önlemek için, giriş olarak beklenen boyutu belirtir.</span><span class="sxs-lookup"><span data-stu-id="28090-121">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="28090-122">`pwzVersion`Null ise, `pcchVersion` `pwzVersion` `GetRequestedRuntime` ön ayırmaya izin vermek için, geri dönüşün beklenen boyutunu içerir; Aksi takdirde, `pcchVersion` üzerine yazılan karakter sayısını içerir `pwzVersion` .</span><span class="sxs-lookup"><span data-stu-id="28090-122">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="28090-123">dışı Seçim.</span><span class="sxs-lookup"><span data-stu-id="28090-123">[out] Optional.</span></span> <span data-ttu-id="28090-124">`GetRequestedRuntime`Döndüğünde, döndürülen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) ARABIRIMINE karşılık gelen CLR sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="28090-124">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="28090-125">[in, out] Seçim.</span><span class="sxs-lookup"><span data-stu-id="28090-125">[in, out] Optional.</span></span> <span data-ttu-id="28090-126">`pwzImageVersion`Arabellek taşmalarını önlemek için giriş olarak boyutu belirtir.</span><span class="sxs-lookup"><span data-stu-id="28090-126">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="28090-127">`pwzImageVersion`Null ise, `pcchImageVersion` `pwzImageVersion` `GetRequestedRuntime` ön ayırmaya izin vermek için, geri dönüşün gereken boyutunu içerir.</span><span class="sxs-lookup"><span data-stu-id="28090-127">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="28090-128">dışı Seçim.</span><span class="sxs-lookup"><span data-stu-id="28090-128">[out] Optional.</span></span> <span data-ttu-id="28090-129">`GetRequestedRuntime`Bağlama işlemi sırasında bir yapılandırma dosyası kullanıyorsa, bu, öğesini döndürdüğünde, `pdwConfigFlags` öğesinde öznitelik ayarlanmış olup olmadığını belirten bir [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) değeri [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) `useLegacyV2RuntimeActivationPolicy` ve özniteliği değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="28090-129">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="28090-130">İle [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) `pdwConfigFlags` ilgili değerleri almak için METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK maskesini uygulayın `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="28090-130">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="28090-131">'ndaki İstenen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi için IID_ICLRRuntimeInfo arabirim tanımlayıcısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="28090-131">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="28090-132">dışı `GetRequestedRuntime`Döndüğünde, karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="28090-132">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="28090-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28090-133">Remarks</span></span>

<span data-ttu-id="28090-134">Bu yöntem başarılı olduğunda, ek bayrakları, döndürülen çalışma zamanı arabiriminin geçerli varsayılan başlatma bayraklarıyla birleştirmenin yan etkisi vardır ve yalnızca, bölüm içindeki yapılandırma akışında aşağıdaki öğelerden biri veya birkaçı varsa `<configuration><runtime>` :</span><span class="sxs-lookup"><span data-stu-id="28090-134">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="28090-135">`<gcServer enabled="true"/>``STARTUP_SERVER_GC`ayarlanmasının nedeni.</span><span class="sxs-lookup"><span data-stu-id="28090-135">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="28090-136">`<etwEnable enabled="true"/>``STARTUP_ETW`ayarlanmasının nedeni.</span><span class="sxs-lookup"><span data-stu-id="28090-136">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="28090-137">`<appDomainResourceMonitoring enabled="true"/>``STARTUP_ARM`ayarlanmasının nedeni.</span><span class="sxs-lookup"><span data-stu-id="28090-137">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="28090-138">Elde edilen varsayılan `STARTUP_FLAGS` değer, yukarıdaki listeden varsayılan başlangıç bayraklarıyla ayarlanan değerlerin bit SEVIYESINDE veya birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="28090-138">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="28090-139">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="28090-139">Return Value</span></span>

<span data-ttu-id="28090-140">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="28090-140">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="28090-141">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28090-141">HRESULT</span></span>|<span data-ttu-id="28090-142">Description</span><span class="sxs-lookup"><span data-stu-id="28090-142">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="28090-143">S_OK</span><span class="sxs-lookup"><span data-stu-id="28090-143">S_OK</span></span>|<span data-ttu-id="28090-144">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="28090-144">The method completed successfully.</span></span>|
|<span data-ttu-id="28090-145">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="28090-145">E_POINTER</span></span>|<span data-ttu-id="28090-146">`pwzVersion`null değil ve `pcchVersion` null.</span><span class="sxs-lookup"><span data-stu-id="28090-146">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="28090-147">-veya-</span><span class="sxs-lookup"><span data-stu-id="28090-147">-or-</span></span><br /><br /> <span data-ttu-id="28090-148">`pwzImageVersion`null değil ve `pcchImageVersion` null.</span><span class="sxs-lookup"><span data-stu-id="28090-148">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="28090-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="28090-149">E_INVALIDARG</span></span>|<span data-ttu-id="28090-150">`dwPolicyFlags`belirtmiyor `METAHOST_POLICY_HIGHCOMPAT` .</span><span class="sxs-lookup"><span data-stu-id="28090-150">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="28090-151">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="28090-151">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="28090-152">Ayrılan bellek `pwzVersion` yetersiz.</span><span class="sxs-lookup"><span data-stu-id="28090-152">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="28090-153">-veya-</span><span class="sxs-lookup"><span data-stu-id="28090-153">-or-</span></span><br /><br /> <span data-ttu-id="28090-154">Ayrılan bellek `pwzImageVersion` yetersiz.</span><span class="sxs-lookup"><span data-stu-id="28090-154">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="28090-155">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="28090-155">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="28090-156">`dwPolicyFlags`METAHOST_POLICY_APPLY_UPGRADE_POLICY içerir ve her ikisi `pwzVersion` de `pcchVersion` null.</span><span class="sxs-lookup"><span data-stu-id="28090-156">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="28090-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28090-157">Requirements</span></span>

<span data-ttu-id="28090-158">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28090-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="28090-159">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="28090-159">**Header:** MetaHost.h</span></span>

<span data-ttu-id="28090-160">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="28090-160">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="28090-161">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28090-161">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="28090-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28090-162">See also</span></span>

- [<span data-ttu-id="28090-163">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28090-163">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="28090-164">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="28090-164">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="28090-165">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="28090-165">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="28090-166">Hosting</span><span class="sxs-lookup"><span data-stu-id="28090-166">Hosting</span></span>](index.md)
