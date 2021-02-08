---
description: ': ICLRRuntimeInfo:: LoadErrorString yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0523b5b89072db50c83c52065c22e9df7167a027
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785074"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="c97e7-103">ICLRRuntimeInfo::LoadErrorString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c97e7-103">ICLRRuntimeInfo::LoadErrorString Method</span></span>

<span data-ttu-id="c97e7-104">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="c97e7-104">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="c97e7-105">Bu yöntem aşağıdaki işlevlerin yerini alır:</span><span class="sxs-lookup"><span data-stu-id="c97e7-105">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="c97e7-106">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="c97e7-106">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="c97e7-107">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="c97e7-107">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="c97e7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c97e7-108">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c97e7-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c97e7-109">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="c97e7-110">'ndaki Çevrilecek HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c97e7-110">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="c97e7-111">dışı Verilen HRESULT ile ilişkilendirilen ileti dizesi.</span><span class="sxs-lookup"><span data-stu-id="c97e7-111">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="c97e7-112">[in, out] `pwzbuffer` Arabellek taşmalarını önlemek için boyutu.</span><span class="sxs-lookup"><span data-stu-id="c97e7-112">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="c97e7-113">`pwzbuffer`Null ise, `pcchBuffer` `pwzbuffer` ön ayırmaya izin vermek için beklenen boyutunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c97e7-113">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="c97e7-114">'ndaki Kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c97e7-114">[in] The culture identifier.</span></span> <span data-ttu-id="c97e7-115">Varsayılan kültürü kullanmak için-1 ' i belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c97e7-115">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c97e7-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c97e7-116">Return Value</span></span>  

 <span data-ttu-id="c97e7-117">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c97e7-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c97e7-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c97e7-118">HRESULT</span></span>|<span data-ttu-id="c97e7-119">Description</span><span class="sxs-lookup"><span data-stu-id="c97e7-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c97e7-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="c97e7-120">S_OK</span></span>|<span data-ttu-id="c97e7-121">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c97e7-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="c97e7-122">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c97e7-122">E_POINTER</span></span>|<span data-ttu-id="c97e7-123">`pcchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="c97e7-123">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="c97e7-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c97e7-124">E_INVALIDARG</span></span>|<span data-ttu-id="c97e7-125">`pwzBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="c97e7-125">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c97e7-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c97e7-126">Requirements</span></span>  

 <span data-ttu-id="c97e7-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c97e7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c97e7-128">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c97e7-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c97e7-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c97e7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c97e7-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c97e7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97e7-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c97e7-131">See also</span></span>

- [<span data-ttu-id="c97e7-132">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c97e7-132">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c97e7-133">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c97e7-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c97e7-134">Hosting</span><span class="sxs-lookup"><span data-stu-id="c97e7-134">Hosting</span></span>](index.md)
