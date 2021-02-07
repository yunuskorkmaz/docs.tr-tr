---
description: ': ICLRMetaHost:: Enumerateınstalcontroller yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a1c2fe46a64339e013df0f65dc073d183036a0fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689202"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="07ff3-103">ICLRMetaHost::EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07ff3-103">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>

<span data-ttu-id="07ff3-104">Bir bilgisayara yüklenen ortak dil çalışma zamanının (CLR) her sürümü için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="07ff3-104">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ff3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07ff3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07ff3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07ff3-106">Parameters</span></span>  

 `ppEnumerator`  
 <span data-ttu-id="07ff3-107">dışı Bilgisayarda yüklü olan her CLR sürümüne karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimlerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="07ff3-107">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07ff3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07ff3-108">Return Value</span></span>  

 <span data-ttu-id="07ff3-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="07ff3-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="07ff3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07ff3-110">HRESULT</span></span>|<span data-ttu-id="07ff3-111">Description</span><span class="sxs-lookup"><span data-stu-id="07ff3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07ff3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="07ff3-112">S_OK</span></span>|<span data-ttu-id="07ff3-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="07ff3-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="07ff3-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="07ff3-114">E_POINTER</span></span>|<span data-ttu-id="07ff3-115">`ppEnumerator` null.</span><span class="sxs-lookup"><span data-stu-id="07ff3-115">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07ff3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07ff3-116">Requirements</span></span>  

 <span data-ttu-id="07ff3-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07ff3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07ff3-118">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="07ff3-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="07ff3-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="07ff3-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07ff3-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07ff3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ff3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07ff3-121">See also</span></span>

- [<span data-ttu-id="07ff3-122">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07ff3-122">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="07ff3-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="07ff3-123">Hosting</span></span>](index.md)
