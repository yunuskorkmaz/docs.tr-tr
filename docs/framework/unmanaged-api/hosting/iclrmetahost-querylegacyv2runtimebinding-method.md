---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: b9a51a85bd17e527d4c04b69ca65100a7069607f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703717"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="c9019-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9019-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="c9019-103">Eski etkinleştirme ilkesinin bağlı olduğu bir çalışma zamanını temsil eden bir arabirim döndürür. Örneğin, `useLegacyV2RuntimeActivationPolicy` [ \< Başlangıç> öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası girişinde, eski etkinleştirme API 'Lerinin doğrudan kullanımıyla veya [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemini çağırarak.</span><span class="sxs-lookup"><span data-stu-id="c9019-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9019-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c9019-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9019-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9019-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="c9019-106">'ndaki Gerekli. Şu anda bu parametre için geçerli olan tek değer `IID_ICLRRuntimeInfo` .</span><span class="sxs-lookup"><span data-stu-id="c9019-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="c9019-107">dışı Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c9019-107">[out] Required.</span></span> <span data-ttu-id="c9019-108">Bu yöntem döndüğünde, eski etkinleştirme ilkesine bağlanan bir çalışma zamanını temsil eden [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine yönelik bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="c9019-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9019-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c9019-109">Return Value</span></span>  
 <span data-ttu-id="c9019-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c9019-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c9019-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9019-111">HRESULT</span></span>|<span data-ttu-id="c9019-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9019-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9019-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9019-113">S_OK</span></span>|<span data-ttu-id="c9019-114">Yöntem başarıyla tamamlandı ve eski etkinleştirme ilkesine bağlanan bir çalışma zamanı döndürdü.</span><span class="sxs-lookup"><span data-stu-id="c9019-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="c9019-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c9019-115">S_FALSE</span></span>|<span data-ttu-id="c9019-116">Yöntem başarıyla tamamlandı, ancak eski bir çalışma zamanı henüz bağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="c9019-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="c9019-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="c9019-117">E_NOINTERFACE</span></span>|<span data-ttu-id="c9019-118">Yöntem, eski etkinleştirme ilkesine bağlanan, ancak `riid` Bu çalışma zamanı tarafından desteklenmeyen bir çalışma zamanı buldu.</span><span class="sxs-lookup"><span data-stu-id="c9019-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9019-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9019-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9019-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9019-120">Requirements</span></span>  
 <span data-ttu-id="c9019-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9019-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9019-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c9019-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c9019-123">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c9019-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9019-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9019-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9019-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9019-125">See also</span></span>

- [<span data-ttu-id="c9019-126">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9019-126">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="c9019-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="c9019-127">Hosting</span></span>](index.md)
