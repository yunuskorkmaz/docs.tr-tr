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
ms.openlocfilehash: e1b8af06a52a3961bb3e551375350dee849343b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="2a1c6-102">ICLRRuntimeInfo::GetProcAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="2a1c6-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="2a1c6-103">Bu arabirim ile ilişkili ortak dil çalışma zamanı (CLR) dışarı aktarılan belirtilen bir işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="2a1c6-104">Bu yöntem yerini [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1c6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a1c6-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a1c6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a1c6-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="2a1c6-107">[in] Verilen işlevin adı.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="2a1c6-108">[out] Dışarı aktarılan işlev adresi.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a1c6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2a1c6-109">Return Value</span></span>  
 <span data-ttu-id="2a1c6-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2a1c6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a1c6-111">HRESULT</span></span>|<span data-ttu-id="2a1c6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a1c6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a1c6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a1c6-113">S_OK</span></span>|<span data-ttu-id="2a1c6-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="2a1c6-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2a1c6-115">E_POINTER</span></span>|<span data-ttu-id="2a1c6-116">`pszProcName`veya `ppProc` null.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="2a1c6-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="2a1c6-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="2a1c6-118">Belirtilen işlev, dışarı aktarılan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a1c6-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a1c6-119">Remarks</span></span>  
 <span data-ttu-id="2a1c6-120">Bu yöntem yüklendi ancak başlatılmadı CLR neden olur.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a1c6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a1c6-121">Requirements</span></span>  
 <span data-ttu-id="2a1c6-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a1c6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a1c6-123">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2a1c6-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2a1c6-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2a1c6-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a1c6-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a1c6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a1c6-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a1c6-126">See Also</span></span>  
 [<span data-ttu-id="2a1c6-127">Iclrruntimeınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a1c6-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="2a1c6-128">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2a1c6-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="2a1c6-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="2a1c6-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
