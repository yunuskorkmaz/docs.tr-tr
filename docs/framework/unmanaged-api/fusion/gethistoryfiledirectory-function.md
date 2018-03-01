---
title: "GetHistoryFileDirectory İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d0ec18a4f95d0d280a66b3b9d9200c560f5f187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="7321f-102">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="7321f-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="7321f-103">Uygulama geçmişi dizinin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="7321f-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7321f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7321f-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7321f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7321f-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="7321f-106">[out] Yol uygulama geçmiş dizinine tutmak için arabellek.</span><span class="sxs-lookup"><span data-stu-id="7321f-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="7321f-107">[içinde out] Arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="7321f-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7321f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7321f-108">Return Value</span></span>  
 <span data-ttu-id="7321f-109">Bu yöntem, aşağıdaki değerleri yanı sıra Winerror.h'de dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7321f-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="7321f-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="7321f-110">Return code</span></span>|<span data-ttu-id="7321f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7321f-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7321f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7321f-112">S_OK</span></span>|<span data-ttu-id="7321f-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7321f-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="7321f-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7321f-114">E_INVALIDARG</span></span>|<span data-ttu-id="7321f-115">`wzDir`veya `pdwSize` null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="7321f-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7321f-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7321f-116">Remarks</span></span>  
 <span data-ttu-id="7321f-117">Başarıyla tamamlandığında, `pdwSize` bağımsız değişkenini yolu dize uzunluğu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7321f-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7321f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7321f-118">Requirements</span></span>  
 <span data-ttu-id="7321f-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7321f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7321f-120">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7321f-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7321f-121">**Kitaplığı:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="7321f-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="7321f-122">Fusion.dll Mscorwks.dll yerine .NET Framework'ün doğru sürümünü hedef emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7321f-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="7321f-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7321f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7321f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7321f-124">See Also</span></span>  
 [<span data-ttu-id="7321f-125">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="7321f-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="7321f-126">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="7321f-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="7321f-127">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7321f-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
