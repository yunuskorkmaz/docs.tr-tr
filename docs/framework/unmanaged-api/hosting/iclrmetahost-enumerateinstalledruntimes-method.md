---
title: "ICLRMetaHost::EnumerateInstalledRuntimes Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.EnumerateInstalledRuntimes
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0229aa5a80100d9793459473794d341e7d548ca2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="e2bdf-102">ICLRMetaHost::EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2bdf-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="e2bdf-103">Geçerli bir içeren bir numaralandırmayı döndüren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) her bir bilgisayarda yüklü olan ortak dil çalışma zamanı (CLR) sürümü için arabirim.</span><span class="sxs-lookup"><span data-stu-id="e2bdf-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2bdf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2bdf-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2bdf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2bdf-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="e2bdf-106">[out] Sabit listesi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) her bilgisayarda yüklü CLR sürümü ile eşleşen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="e2bdf-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2bdf-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e2bdf-107">Return Value</span></span>  
 <span data-ttu-id="e2bdf-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e2bdf-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e2bdf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2bdf-109">HRESULT</span></span>|<span data-ttu-id="e2bdf-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2bdf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2bdf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2bdf-111">S_OK</span></span>|<span data-ttu-id="e2bdf-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e2bdf-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="e2bdf-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e2bdf-113">E_POINTER</span></span>|<span data-ttu-id="e2bdf-114">`ppEnumerator`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e2bdf-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2bdf-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2bdf-115">Requirements</span></span>  
 <span data-ttu-id="e2bdf-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2bdf-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2bdf-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e2bdf-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e2bdf-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e2bdf-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2bdf-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2bdf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2bdf-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2bdf-120">See Also</span></span>  
 [<span data-ttu-id="e2bdf-121">Iclrmetahost arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2bdf-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="e2bdf-122">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e2bdf-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
