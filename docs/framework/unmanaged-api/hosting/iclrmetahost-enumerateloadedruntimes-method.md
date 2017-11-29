---
title: "ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.EnumerateLoadedRuntimes
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0724bf44eaf82b39262876ea4a44509b6c7d576
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="e2e97-102">ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2e97-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="e2e97-103">Geçerli bir içeren bir numaralandırmayı döndüren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) verilen bir işlem olarak yüklenen ortak dil çalışma zamanı (CLR) her sürümü için arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e2e97-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="e2e97-104">Bu yöntem yerini [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="e2e97-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e97-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2e97-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2e97-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2e97-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="e2e97-107">[in] Yüklenen çalışma zamanları için incelemek için işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="e2e97-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="e2e97-108">[out] Bir <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` numaralandırması [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) işlemi tarafından yüklenen her CLR karşılık gelen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="e2e97-108">[out] An <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2e97-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e2e97-109">Return Value</span></span>  
 <span data-ttu-id="e2e97-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e2e97-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e2e97-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2e97-111">HRESULT</span></span>|<span data-ttu-id="e2e97-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2e97-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2e97-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2e97-113">S_OK</span></span>|<span data-ttu-id="e2e97-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e2e97-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="e2e97-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e2e97-115">E_POINTER</span></span>|<span data-ttu-id="e2e97-116">`ppEnumerator`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e2e97-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2e97-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2e97-117">Remarks</span></span>  
 <span data-ttu-id="e2e97-118">Kullanım dışı işlevlerle gibi yüklenmiş olsa bile bu listeleri tüm yüklenen çalışma zamanları yöntemdir [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="e2e97-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2e97-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2e97-119">Requirements</span></span>  
 <span data-ttu-id="e2e97-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2e97-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2e97-121">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e2e97-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e2e97-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e2e97-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2e97-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2e97-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e97-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e97-124">See Also</span></span>  
 [<span data-ttu-id="e2e97-125">Iclrmetahost arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2e97-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="e2e97-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e2e97-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
