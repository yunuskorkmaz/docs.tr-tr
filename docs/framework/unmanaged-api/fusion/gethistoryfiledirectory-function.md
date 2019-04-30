---
title: GetHistoryFileDirectory İşlevi
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b60dde31707175a27d2dc6c50484d6089adaeaa6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697631"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="e16de-102">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="e16de-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="e16de-103">Uygulama geçmişi dizininin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="e16de-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e16de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e16de-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e16de-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e16de-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="e16de-106">[out] Yol uygulama geçmiş dizinine tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="e16de-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="e16de-107">[out içinde] Arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e16de-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e16de-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e16de-108">Return Value</span></span>  
 <span data-ttu-id="e16de-109">Bu yöntem, aşağıdaki değerlere ek olarak Wınerror dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e16de-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="e16de-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="e16de-110">Return code</span></span>|<span data-ttu-id="e16de-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e16de-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e16de-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e16de-112">S_OK</span></span>|<span data-ttu-id="e16de-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e16de-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="e16de-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e16de-114">E_INVALIDARG</span></span>|<span data-ttu-id="e16de-115">`wzDir` veya `pdwSize` null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="e16de-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e16de-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e16de-116">Remarks</span></span>  
 <span data-ttu-id="e16de-117">Başarıyla tamamlandığında, `pdwSize` bağımsız değişkeni yol dizesini uzunluğunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e16de-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e16de-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e16de-118">Requirements</span></span>  
 <span data-ttu-id="e16de-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e16de-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e16de-120">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e16de-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e16de-121">**Kitaplığı:** Fusion.dll ve kullanımda olan mscorwks.dll'ye.</span><span class="sxs-lookup"><span data-stu-id="e16de-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="e16de-122">Fusion.dll yerine Mscorwks.dll doğru .NET Framework sürümünü hedefleyen emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e16de-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e16de-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e16de-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16de-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e16de-124">See also</span></span>

- [<span data-ttu-id="e16de-125">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="e16de-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="e16de-126">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="e16de-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="e16de-127">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e16de-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
