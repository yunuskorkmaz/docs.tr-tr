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
ms.openlocfilehash: f8f67edde7f99878429ca0bbd89aaf52336aa79c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730454"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="63254-102">ICLRMetaHost::EnumerateInstalledRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63254-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>

<span data-ttu-id="63254-103">Bir bilgisayara yüklenen ortak dil çalışma zamanının (CLR) her sürümü için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="63254-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63254-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="63254-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63254-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63254-105">Parameters</span></span>  

 `ppEnumerator`  
 <span data-ttu-id="63254-106">dışı Bilgisayarda yüklü olan her CLR sürümüne karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimlerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="63254-106">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63254-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63254-107">Return Value</span></span>  

 <span data-ttu-id="63254-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="63254-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="63254-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63254-109">HRESULT</span></span>|<span data-ttu-id="63254-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63254-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63254-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="63254-111">S_OK</span></span>|<span data-ttu-id="63254-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="63254-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="63254-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="63254-113">E_POINTER</span></span>|<span data-ttu-id="63254-114">`ppEnumerator` null.</span><span class="sxs-lookup"><span data-stu-id="63254-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63254-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63254-115">Requirements</span></span>  

 <span data-ttu-id="63254-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63254-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63254-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="63254-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="63254-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="63254-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63254-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63254-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63254-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63254-120">See also</span></span>

- [<span data-ttu-id="63254-121">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63254-121">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="63254-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="63254-122">Hosting</span></span>](index.md)
