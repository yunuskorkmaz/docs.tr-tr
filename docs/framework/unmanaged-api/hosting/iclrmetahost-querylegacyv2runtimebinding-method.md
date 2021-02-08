---
description: ': ICLRMetaHost:: QueryLegacyV2RuntimeBinding yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ae825c2b2dfe2ce5b75ac9b82511215704fa357f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789859"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="25311-103">ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25311-103">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>

<span data-ttu-id="25311-104">Eski etkinleştirme ilkesinin bağlı olduğu bir çalışma zamanını temsil eden bir arabirim döndürür. Örneğin, `useLegacyV2RuntimeActivationPolicy` [ \<startup> öğe](../../configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası girişinde özniteliği kullanarak, eski etkinleştirme API 'Lerinin doğrudan kullanımını veya [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemini çağırarak.</span><span class="sxs-lookup"><span data-stu-id="25311-104">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25311-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25311-105">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25311-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25311-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="25311-107">'ndaki Gerekli. Şu anda bu parametre için geçerli olan tek değer `IID_ICLRRuntimeInfo` .</span><span class="sxs-lookup"><span data-stu-id="25311-107">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="25311-108">dışı Gerekli.</span><span class="sxs-lookup"><span data-stu-id="25311-108">[out] Required.</span></span> <span data-ttu-id="25311-109">Bu yöntem döndüğünde, eski etkinleştirme ilkesine bağlanan bir çalışma zamanını temsil eden [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine yönelik bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="25311-109">When this method returns, contains a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25311-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25311-110">Return Value</span></span>  

 <span data-ttu-id="25311-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="25311-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="25311-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25311-112">HRESULT</span></span>|<span data-ttu-id="25311-113">Description</span><span class="sxs-lookup"><span data-stu-id="25311-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25311-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="25311-114">S_OK</span></span>|<span data-ttu-id="25311-115">Yöntem başarıyla tamamlandı ve eski etkinleştirme ilkesine bağlanan bir çalışma zamanı döndürdü.</span><span class="sxs-lookup"><span data-stu-id="25311-115">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="25311-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="25311-116">S_FALSE</span></span>|<span data-ttu-id="25311-117">Yöntem başarıyla tamamlandı, ancak eski bir çalışma zamanı henüz bağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="25311-117">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="25311-118">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="25311-118">E_NOINTERFACE</span></span>|<span data-ttu-id="25311-119">Yöntem, eski etkinleştirme ilkesine bağlanan, ancak `riid` Bu çalışma zamanı tarafından desteklenmeyen bir çalışma zamanı buldu.</span><span class="sxs-lookup"><span data-stu-id="25311-119">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25311-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25311-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25311-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25311-121">Requirements</span></span>  

 <span data-ttu-id="25311-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25311-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25311-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="25311-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="25311-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="25311-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25311-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25311-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25311-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25311-126">See also</span></span>

- [<span data-ttu-id="25311-127">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25311-127">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="25311-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="25311-128">Hosting</span></span>](index.md)
