---
description: ': ICLRMetaHostPolicy:: GetRequestedRuntime yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0e11694b0cb66ad7fc28abf7bb9f7fc8c6931a19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789846"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="2bcea-103">ICLRMetaHostPolicy::GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2bcea-103">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="2bcea-104">Bir barındırma ilkesi, yönetilen derleme, sürüm dizesi ve yapılandırma akışı temelinde ortak dil çalışma zamanının (CLR) tercih edilen bir sürümüne arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bcea-104">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="2bcea-105">Bu yöntem, CLR 'yi gerçekten yüklemez veya etkinleştirmez, ancak ilke sonucunu temsil eden [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimini geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2bcea-105">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="2bcea-106">Bu yöntem, [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)ve [GetCORRequiredVersion](getcorrequiredversion-function.md) yöntemlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="2bcea-106">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="2bcea-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bcea-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="2bcea-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bcea-108">Parameters</span></span>

|<span data-ttu-id="2bcea-109">Ad</span><span class="sxs-lookup"><span data-stu-id="2bcea-109">Name</span></span>|<span data-ttu-id="2bcea-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bcea-110">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="2bcea-111">'ndaki Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2bcea-111">[in] Required.</span></span> <span data-ttu-id="2bcea-112">Bir bağlama ilkesini ve herhangi bir sayıda değiştiriciyi temsil eden [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) numaralandırması üyesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-112">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="2bcea-113">Şu anda kullanılabilir olan tek ilke [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2bcea-113">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="2bcea-114">Değiştiriciler [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)ve [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-114">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="2bcea-115">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="2bcea-115">[in] Optional.</span></span> <span data-ttu-id="2bcea-116">Derleme dosyası yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-116">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="2bcea-117">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="2bcea-117">[in] Optional.</span></span> <span data-ttu-id="2bcea-118">Yapılandırma dosyasını bir olarak belirtir <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2bcea-118">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="2bcea-119">[in, out] Seçim.</span><span class="sxs-lookup"><span data-stu-id="2bcea-119">[in, out] Optional.</span></span> <span data-ttu-id="2bcea-120">Yüklenecek tercih edilen CLR sürümünü belirtir veya döndürür.</span><span class="sxs-lookup"><span data-stu-id="2bcea-120">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="2bcea-121">[in, out] Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2bcea-121">[in, out] Required.</span></span> <span data-ttu-id="2bcea-122">`pwzVersion`Arabellek taşmalarını önlemek için, giriş olarak beklenen boyutu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-122">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="2bcea-123">`pwzVersion`Null ise, `pcchVersion` `pwzVersion` `GetRequestedRuntime` ön ayırmaya izin vermek için, geri dönüşün beklenen boyutunu içerir; Aksi takdirde, `pcchVersion` üzerine yazılan karakter sayısını içerir `pwzVersion` .</span><span class="sxs-lookup"><span data-stu-id="2bcea-123">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="2bcea-124">dışı Seçim.</span><span class="sxs-lookup"><span data-stu-id="2bcea-124">[out] Optional.</span></span> <span data-ttu-id="2bcea-125">`GetRequestedRuntime`Döndüğünde, döndürülen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) ARABIRIMINE karşılık gelen CLR sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-125">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="2bcea-126">[in, out] Seçim.</span><span class="sxs-lookup"><span data-stu-id="2bcea-126">[in, out] Optional.</span></span> <span data-ttu-id="2bcea-127">`pwzImageVersion`Arabellek taşmalarını önlemek için giriş olarak boyutu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-127">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="2bcea-128">`pwzImageVersion`Null ise, `pcchImageVersion` `pwzImageVersion` `GetRequestedRuntime` ön ayırmaya izin vermek için, geri dönüşün gereken boyutunu içerir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-128">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="2bcea-129">dışı Seçim.</span><span class="sxs-lookup"><span data-stu-id="2bcea-129">[out] Optional.</span></span> <span data-ttu-id="2bcea-130">`GetRequestedRuntime`Bağlama işlemi sırasında bir yapılandırma dosyası kullanıyorsa, bu, öğesini döndürdüğünde, `pdwConfigFlags` öğesinde öznitelik ayarlanmış olup olmadığını belirten bir [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) değeri [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) `useLegacyV2RuntimeActivationPolicy` ve özniteliği değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-130">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="2bcea-131">İle [](metahost-config-flags-enumeration.md) `pdwConfigFlags` ilgili değerleri almak için METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK maskesini uygulayın `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="2bcea-131">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="2bcea-132">'ndaki İstenen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi için IID_ICLRRuntimeInfo arabirim tanımlayıcısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-132">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="2bcea-133">dışı `GetRequestedRuntime` Döndüğünde, karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-133">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2bcea-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2bcea-134">Remarks</span></span>

<span data-ttu-id="2bcea-135">Bu yöntem başarılı olduğunda, ek bayrakları, döndürülen çalışma zamanı arabiriminin geçerli varsayılan başlatma bayraklarıyla birleştirmenin yan etkisi vardır ve yalnızca, bölüm içindeki yapılandırma akışında aşağıdaki öğelerden biri veya birkaçı varsa `<configuration><runtime>` :</span><span class="sxs-lookup"><span data-stu-id="2bcea-135">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="2bcea-136">`<gcServer enabled="true"/>``STARTUP_SERVER_GC`ayarlanmasının nedeni.</span><span class="sxs-lookup"><span data-stu-id="2bcea-136">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="2bcea-137">`<etwEnable enabled="true"/>``STARTUP_ETW`ayarlanmasının nedeni.</span><span class="sxs-lookup"><span data-stu-id="2bcea-137">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="2bcea-138">`<appDomainResourceMonitoring enabled="true"/>``STARTUP_ARM`ayarlanmasının nedeni.</span><span class="sxs-lookup"><span data-stu-id="2bcea-138">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="2bcea-139">Elde edilen varsayılan `STARTUP_FLAGS` değer, yukarıdaki listeden varsayılan başlangıç bayraklarıyla ayarlanan değerlerin bit SEVIYESINDE veya birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="2bcea-139">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="2bcea-140">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2bcea-140">Return Value</span></span>

<span data-ttu-id="2bcea-141">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="2bcea-141">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="2bcea-142">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2bcea-142">HRESULT</span></span>|<span data-ttu-id="2bcea-143">Description</span><span class="sxs-lookup"><span data-stu-id="2bcea-143">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="2bcea-144">S_OK</span><span class="sxs-lookup"><span data-stu-id="2bcea-144">S_OK</span></span>|<span data-ttu-id="2bcea-145">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2bcea-145">The method completed successfully.</span></span>|
|<span data-ttu-id="2bcea-146">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2bcea-146">E_POINTER</span></span>|<span data-ttu-id="2bcea-147">`pwzVersion` null değil ve `pcchVersion` null.</span><span class="sxs-lookup"><span data-stu-id="2bcea-147">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="2bcea-148">-veya-</span><span class="sxs-lookup"><span data-stu-id="2bcea-148">-or-</span></span><br /><br /> <span data-ttu-id="2bcea-149">`pwzImageVersion` null değil ve `pcchImageVersion` null.</span><span class="sxs-lookup"><span data-stu-id="2bcea-149">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="2bcea-150">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2bcea-150">E_INVALIDARG</span></span>|<span data-ttu-id="2bcea-151">`dwPolicyFlags` belirtmiyor `METAHOST_POLICY_HIGHCOMPAT` .</span><span class="sxs-lookup"><span data-stu-id="2bcea-151">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="2bcea-152">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2bcea-152">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2bcea-153">Ayrılan bellek `pwzVersion` yetersiz.</span><span class="sxs-lookup"><span data-stu-id="2bcea-153">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="2bcea-154">-veya-</span><span class="sxs-lookup"><span data-stu-id="2bcea-154">-or-</span></span><br /><br /> <span data-ttu-id="2bcea-155">Ayrılan bellek `pwzImageVersion` yetersiz.</span><span class="sxs-lookup"><span data-stu-id="2bcea-155">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="2bcea-156">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="2bcea-156">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="2bcea-157">`dwPolicyFlags` METAHOST_POLICY_APPLY_UPGRADE_POLICY içerir ve her ikisi `pwzVersion` de `pcchVersion` null.</span><span class="sxs-lookup"><span data-stu-id="2bcea-157">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="2bcea-158">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bcea-158">Requirements</span></span>

<span data-ttu-id="2bcea-159">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bcea-159">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2bcea-160">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="2bcea-160">**Header:** MetaHost.h</span></span>

<span data-ttu-id="2bcea-161">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2bcea-161">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="2bcea-162">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bcea-162">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2bcea-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bcea-163">See also</span></span>

- [<span data-ttu-id="2bcea-164">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bcea-164">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="2bcea-165">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2bcea-165">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="2bcea-166">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2bcea-166">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="2bcea-167">Hosting</span><span class="sxs-lookup"><span data-stu-id="2bcea-167">Hosting</span></span>](index.md)
