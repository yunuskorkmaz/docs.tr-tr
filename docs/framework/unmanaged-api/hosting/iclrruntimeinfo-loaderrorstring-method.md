---
title: ICLRRuntimeInfo::LoadErrorString Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
ms.openlocfilehash: 20f2041599e85b8df20a7a9cf44680da9f17244e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195936"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="fba62-102">ICLRRuntimeInfo::LoadErrorString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fba62-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="fba62-103">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="fba62-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="fba62-104">Bu yöntem aşağıdaki işlevlerin yerini alır:</span><span class="sxs-lookup"><span data-stu-id="fba62-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="fba62-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="fba62-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [<span data-ttu-id="fba62-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="fba62-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="fba62-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fba62-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fba62-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fba62-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="fba62-109">'ndaki Çevrilecek HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fba62-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="fba62-110">dışı Verilen HRESULT ile ilişkilendirilen ileti dizesi.</span><span class="sxs-lookup"><span data-stu-id="fba62-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="fba62-111">[in, out] Arabellek taşmalarını önlemek için `pwzbuffer` boyutu.</span><span class="sxs-lookup"><span data-stu-id="fba62-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="fba62-112">`pwzbuffer` null ise, `pcchBuffer`, ön ayırmaya izin vermek için beklenen `pwzbuffer` boyutunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="fba62-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="fba62-113">'ndaki Kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="fba62-113">[in] The culture identifier.</span></span> <span data-ttu-id="fba62-114">Varsayılan kültürü kullanmak için-1 ' i belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fba62-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fba62-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fba62-115">Return Value</span></span>  
 <span data-ttu-id="fba62-116">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="fba62-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fba62-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fba62-117">HRESULT</span></span>|<span data-ttu-id="fba62-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fba62-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fba62-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="fba62-119">S_OK</span></span>|<span data-ttu-id="fba62-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="fba62-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="fba62-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fba62-121">E_POINTER</span></span>|<span data-ttu-id="fba62-122">`pcchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="fba62-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="fba62-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fba62-123">E_INVALIDARG</span></span>|<span data-ttu-id="fba62-124">`pwzBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="fba62-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fba62-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fba62-125">Requirements</span></span>  
 <span data-ttu-id="fba62-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fba62-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fba62-127">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="fba62-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fba62-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fba62-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fba62-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fba62-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba62-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fba62-130">See also</span></span>

- [<span data-ttu-id="fba62-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fba62-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="fba62-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fba62-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="fba62-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="fba62-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
