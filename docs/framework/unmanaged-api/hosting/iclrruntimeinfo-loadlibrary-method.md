---
title: "ICLRRuntimeInfo::LoadLibrary Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadLibrary
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b688a4f2557c5ab2ef112e13b411e25ad47b8c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="07de8-102">ICLRRuntimeInfo::LoadLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07de8-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="07de8-103">.NET Framework kitaplığı tarafından temsil edilen ortak dil çalışma zamanı (CLR) yükler bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="07de8-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="07de8-104">Bu yöntem yerini [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="07de8-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07de8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07de8-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07de8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07de8-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="07de8-107">[in] Yüklenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="07de8-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="07de8-108">[out] Yüklenen derleme için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="07de8-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07de8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07de8-109">Return Value</span></span>  
 <span data-ttu-id="07de8-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="07de8-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="07de8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07de8-111">HRESULT</span></span>|<span data-ttu-id="07de8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07de8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07de8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="07de8-113">S_OK</span></span>|<span data-ttu-id="07de8-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="07de8-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="07de8-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="07de8-115">E_POINTER</span></span>|<span data-ttu-id="07de8-116">`pwzDllName`veya `phndModule` null.</span><span class="sxs-lookup"><span data-stu-id="07de8-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="07de8-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="07de8-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="07de8-118">İsteği işlemek yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="07de8-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07de8-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07de8-119">Remarks</span></span>  
 <span data-ttu-id="07de8-120">Bu yöntem yalnızca .NET Framework yeniden dağıtılabilir paketinde DLL'lerini yükler.</span><span class="sxs-lookup"><span data-stu-id="07de8-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="07de8-121">Kullanıcı tarafından oluşturulan derlemeler yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="07de8-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07de8-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07de8-122">Requirements</span></span>  
 <span data-ttu-id="07de8-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07de8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07de8-124">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="07de8-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="07de8-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="07de8-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07de8-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07de8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07de8-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07de8-127">See Also</span></span>  
 [<span data-ttu-id="07de8-128">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07de8-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="07de8-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="07de8-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="07de8-130">Barındırma</span><span class="sxs-lookup"><span data-stu-id="07de8-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
