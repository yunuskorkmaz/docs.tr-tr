---
title: ICLRRuntimeInfo::GetProcAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetProcAddress
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2878b23a2f848657e1d26b3bfb8395f8897c0632
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="2ea76-102">ICLRRuntimeInfo::GetProcAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="2ea76-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="2ea76-103">Bu arabirim ile ilişkili ortak dil çalışma zamanı (CLR) dışarı aktarılan belirtilen bir işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="2ea76-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="2ea76-104">Bu yöntem yerini [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="2ea76-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea76-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ea76-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ea76-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ea76-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="2ea76-107">[in] Verilen işlevin adı.</span><span class="sxs-lookup"><span data-stu-id="2ea76-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="2ea76-108">[out] Dışarı aktarılan işlev adresi.</span><span class="sxs-lookup"><span data-stu-id="2ea76-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ea76-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2ea76-109">Return Value</span></span>  
 <span data-ttu-id="2ea76-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="2ea76-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2ea76-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ea76-111">HRESULT</span></span>|<span data-ttu-id="2ea76-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ea76-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ea76-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ea76-113">S_OK</span></span>|<span data-ttu-id="2ea76-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2ea76-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="2ea76-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2ea76-115">E_POINTER</span></span>|<span data-ttu-id="2ea76-116">`pszProcName`veya `ppProc` null.</span><span class="sxs-lookup"><span data-stu-id="2ea76-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="2ea76-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="2ea76-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="2ea76-118">Belirtilen işlev, dışarı aktarılan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="2ea76-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ea76-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ea76-119">Remarks</span></span>  
 <span data-ttu-id="2ea76-120">Bu yöntem yüklendi ancak başlatılmadı CLR neden olur.</span><span class="sxs-lookup"><span data-stu-id="2ea76-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ea76-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ea76-121">Requirements</span></span>  
 <span data-ttu-id="2ea76-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ea76-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ea76-123">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2ea76-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2ea76-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2ea76-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ea76-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ea76-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea76-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea76-126">See Also</span></span>  
 [<span data-ttu-id="2ea76-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ea76-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="2ea76-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2ea76-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="2ea76-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="2ea76-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
