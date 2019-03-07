---
title: ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5a0c577975b1c16234fda649b54bcdd9f1ae59e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494885"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="8ccd7-102">ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ccd7-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="8ccd7-103">İçeren geçerli bir sabit listesini döndürür [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) yüklenen verilen bir işlem içinde ortak dil çalışma zamanı (CLR) her sürümü için arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8ccd7-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="8ccd7-104">Bu yöntem yerine geçer [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="8ccd7-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ccd7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ccd7-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ccd7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ccd7-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="8ccd7-107">[in] Yüklenen çalışma zamanlarını incelemek için işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="8ccd7-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="8ccd7-108">[out] Bir <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> numaralandırması [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) işlemi tarafından yüklenen her CLR karşılık gelen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="8ccd7-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ccd7-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ccd7-109">Return Value</span></span>  
 <span data-ttu-id="8ccd7-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8ccd7-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8ccd7-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ccd7-111">HRESULT</span></span>|<span data-ttu-id="8ccd7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ccd7-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ccd7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ccd7-113">S_OK</span></span>|<span data-ttu-id="8ccd7-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8ccd7-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="8ccd7-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8ccd7-115">E_POINTER</span></span>|<span data-ttu-id="8ccd7-116">`ppEnumerator` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="8ccd7-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ccd7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ccd7-117">Remarks</span></span>  
 <span data-ttu-id="8ccd7-118">Kullanım dışı bırakılan işlevler ile gibi yüklenmiş olsa bile bu listeleri yüklenen tüm çalışma zamanları, yöntemdir [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="8ccd7-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ccd7-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ccd7-119">Requirements</span></span>  
 <span data-ttu-id="8ccd7-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ccd7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ccd7-121">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8ccd7-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8ccd7-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8ccd7-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ccd7-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ccd7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccd7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ccd7-124">See also</span></span>
- [<span data-ttu-id="8ccd7-125">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ccd7-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="8ccd7-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="8ccd7-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
