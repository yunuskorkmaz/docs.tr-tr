---
title: ICLRMetaHost::EnumerateInstalledRuntimes Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09931dce7afdb7944cf9912b5146e44fda131935
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993284"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="d9e57-102">ICLRMetaHost::EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9e57-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="d9e57-103">İçeren geçerli bir sabit listesini döndürür [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) her bir bilgisayarda yüklü olan ortak dil çalışma zamanı (CLR) sürümü için arabirim.</span><span class="sxs-lookup"><span data-stu-id="d9e57-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e57-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9e57-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9e57-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9e57-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="d9e57-106">[out] Sabit listesi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) her bilgisayarda yüklü CLR sürümüne karşılık gelen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="d9e57-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e57-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9e57-107">Return Value</span></span>  
 <span data-ttu-id="d9e57-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="d9e57-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d9e57-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9e57-109">HRESULT</span></span>|<span data-ttu-id="d9e57-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9e57-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9e57-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9e57-111">S_OK</span></span>|<span data-ttu-id="d9e57-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d9e57-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="d9e57-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d9e57-113">E_POINTER</span></span>|<span data-ttu-id="d9e57-114">`ppEnumerator` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="d9e57-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9e57-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9e57-115">Requirements</span></span>  
 <span data-ttu-id="d9e57-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e57-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e57-117">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d9e57-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d9e57-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d9e57-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9e57-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e57-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e57-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9e57-120">See also</span></span>

- [<span data-ttu-id="d9e57-121">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9e57-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="d9e57-122">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d9e57-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
