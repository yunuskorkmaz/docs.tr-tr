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
ms.openlocfilehash: 9415d5189edb901822abad9269e0150e7601a963
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140962"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="7d35c-102">ICLRMetaHost::EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d35c-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="7d35c-103">Bir bilgisayara yüklenen ortak dil çalışma zamanının (CLR) her sürümü için geçerli bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d35c-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d35c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d35c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d35c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d35c-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="7d35c-106">dışı Bilgisayarda yüklü olan her CLR sürümüne karşılık gelen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimlerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="7d35c-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d35c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d35c-107">Return Value</span></span>  
 <span data-ttu-id="7d35c-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d35c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7d35c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d35c-109">HRESULT</span></span>|<span data-ttu-id="7d35c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d35c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d35c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d35c-111">S_OK</span></span>|<span data-ttu-id="7d35c-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7d35c-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="7d35c-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7d35c-113">E_POINTER</span></span>|<span data-ttu-id="7d35c-114">`ppEnumerator` null.</span><span class="sxs-lookup"><span data-stu-id="7d35c-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d35c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d35c-115">Requirements</span></span>  
 <span data-ttu-id="7d35c-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d35c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d35c-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7d35c-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d35c-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7d35c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d35c-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d35c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d35c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d35c-120">See also</span></span>

- [<span data-ttu-id="7d35c-121">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d35c-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="7d35c-122">Barındırma</span><span class="sxs-lookup"><span data-stu-id="7d35c-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
