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
ms.openlocfilehash: 0e029aa848a6630ae00c834dd2b924dc4ebce537
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671778"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="23f93-102">ICLRRuntimeInfo::LoadErrorString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23f93-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>

<span data-ttu-id="23f93-103">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="23f93-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="23f93-104">Bu yöntem aşağıdaki işlevlerin yerini alır:</span><span class="sxs-lookup"><span data-stu-id="23f93-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="23f93-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="23f93-105">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="23f93-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="23f93-106">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="23f93-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="23f93-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23f93-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23f93-108">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="23f93-109">'ndaki Çevrilecek HRESULT.</span><span class="sxs-lookup"><span data-stu-id="23f93-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="23f93-110">dışı Verilen HRESULT ile ilişkilendirilen ileti dizesi.</span><span class="sxs-lookup"><span data-stu-id="23f93-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="23f93-111">[in, out] `pwzbuffer` Arabellek taşmalarını önlemek için boyutu.</span><span class="sxs-lookup"><span data-stu-id="23f93-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="23f93-112">`pwzbuffer`Null ise, `pcchBuffer` `pwzbuffer` ön ayırmaya izin vermek için beklenen boyutunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="23f93-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="23f93-113">'ndaki Kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="23f93-113">[in] The culture identifier.</span></span> <span data-ttu-id="23f93-114">Varsayılan kültürü kullanmak için-1 ' i belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="23f93-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23f93-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23f93-115">Return Value</span></span>  

 <span data-ttu-id="23f93-116">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="23f93-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="23f93-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23f93-117">HRESULT</span></span>|<span data-ttu-id="23f93-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23f93-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23f93-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="23f93-119">S_OK</span></span>|<span data-ttu-id="23f93-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="23f93-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="23f93-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="23f93-121">E_POINTER</span></span>|<span data-ttu-id="23f93-122">`pcchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="23f93-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="23f93-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="23f93-123">E_INVALIDARG</span></span>|<span data-ttu-id="23f93-124">`pwzBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="23f93-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23f93-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23f93-125">Requirements</span></span>  

 <span data-ttu-id="23f93-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23f93-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f93-127">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="23f93-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="23f93-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="23f93-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23f93-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f93-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f93-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23f93-130">See also</span></span>

- [<span data-ttu-id="23f93-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23f93-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="23f93-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="23f93-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="23f93-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="23f93-133">Hosting</span></span>](index.md)
