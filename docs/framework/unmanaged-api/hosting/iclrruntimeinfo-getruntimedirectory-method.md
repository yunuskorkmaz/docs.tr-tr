---
title: ICLRRuntimeInfo::GetRuntimeDirectory Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26bee605724fd69d972a7e07c6fe6be2fbcabfa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563866"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="b1c37-102">ICLRRuntimeInfo::GetRuntimeDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="b1c37-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="b1c37-103">Bu arabirimi ile ilişkili ortak dil çalışma zamanı (CLR) yükleme dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="b1c37-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="b1c37-104">Bu yöntem yerine geçer [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .NET Framework sürüm 2.0, 3.0 ve 3.5 içinde sağlanan işlev.</span><span class="sxs-lookup"><span data-stu-id="b1c37-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c37-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1c37-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1c37-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1c37-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="b1c37-107">[out] CLR yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1c37-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="b1c37-108">Yükleme yolu tam olarak; Örneğin, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="b1c37-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="b1c37-109">[out içinde] Boyutunu belirtir `pwzBuffer` arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="b1c37-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="b1c37-110">Varsa `pwzBuffer` boş `pchBuffer` gerekli boyutunu döndürür `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b1c37-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1c37-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1c37-111">Return Value</span></span>  
 <span data-ttu-id="b1c37-112">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="b1c37-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b1c37-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1c37-113">HRESULT</span></span>|<span data-ttu-id="b1c37-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1c37-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1c37-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1c37-115">S_OK</span></span>|<span data-ttu-id="b1c37-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b1c37-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="b1c37-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b1c37-117">E_POINTER</span></span>|<span data-ttu-id="b1c37-118">`pwzBuffer` veya `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="b1c37-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1c37-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1c37-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c37-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1c37-120">Requirements</span></span>  
 <span data-ttu-id="b1c37-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c37-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c37-122">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b1c37-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b1c37-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b1c37-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1c37-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c37-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c37-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1c37-125">See also</span></span>
- [<span data-ttu-id="b1c37-126">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1c37-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="b1c37-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="b1c37-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
