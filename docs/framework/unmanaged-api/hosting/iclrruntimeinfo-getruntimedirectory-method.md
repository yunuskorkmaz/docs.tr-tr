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
ms.openlocfilehash: 5c09f57ad805b4ba17b4bdafd3ced533199277a0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196690"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="b6a75-102">ICLRRuntimeInfo::GetRuntimeDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="b6a75-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="b6a75-103">Bu arabirimi ile ilişkili ortak dil çalışma zamanı (CLR) yükleme dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="b6a75-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="b6a75-104">Bu yöntem yerine geçer [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .NET Framework sürüm 2.0, 3.0 ve 3.5 içinde sağlanan işlev.</span><span class="sxs-lookup"><span data-stu-id="b6a75-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a75-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6a75-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6a75-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6a75-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="b6a75-107">[out] CLR yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6a75-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="b6a75-108">Yükleme yolu tam olarak; Örneğin, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="b6a75-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="b6a75-109">[out içinde] Boyutunu belirtir `pwzBuffer` arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="b6a75-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="b6a75-110">Varsa `pwzBuffer` boş `pchBuffer` gerekli boyutunu döndürür `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b6a75-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6a75-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6a75-111">Return Value</span></span>  
 <span data-ttu-id="b6a75-112">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="b6a75-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b6a75-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6a75-113">HRESULT</span></span>|<span data-ttu-id="b6a75-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6a75-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6a75-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6a75-115">S_OK</span></span>|<span data-ttu-id="b6a75-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b6a75-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="b6a75-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b6a75-117">E_POINTER</span></span>|`pwzBuffer` <span data-ttu-id="b6a75-118">veya `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="b6a75-118">or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6a75-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6a75-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6a75-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6a75-120">Requirements</span></span>  
 <span data-ttu-id="b6a75-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6a75-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6a75-122">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b6a75-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b6a75-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b6a75-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b6a75-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b6a75-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b6a75-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6a75-125">See also</span></span>

- [<span data-ttu-id="b6a75-126">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6a75-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="b6a75-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="b6a75-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
