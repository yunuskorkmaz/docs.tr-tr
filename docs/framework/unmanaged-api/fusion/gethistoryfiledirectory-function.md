---
description: ': GetHistoryFileDirectory Işlevi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 960bc75d69f4be6d1639e109d6327b5e65d3e129
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760972"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="395d7-103">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="395d7-103">GetHistoryFileDirectory Function</span></span>

<span data-ttu-id="395d7-104">Uygulama geçmişi dizininin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="395d7-104">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="395d7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="395d7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="395d7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="395d7-106">Parameters</span></span>  

 `wzDir`  
 <span data-ttu-id="395d7-107">dışı Uygulama geçmişi dizininin yolunu tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="395d7-107">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="395d7-108">[in, out] Arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="395d7-108">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="395d7-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="395d7-109">Return Value</span></span>  

 <span data-ttu-id="395d7-110">Bu yöntem, aşağıdaki değerlere ek olarak WinError. h dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="395d7-110">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="395d7-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="395d7-111">Return code</span></span>|<span data-ttu-id="395d7-112">Description</span><span class="sxs-lookup"><span data-stu-id="395d7-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="395d7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="395d7-113">S_OK</span></span>|<span data-ttu-id="395d7-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="395d7-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="395d7-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="395d7-115">E_INVALIDARG</span></span>|<span data-ttu-id="395d7-116">`wzDir` ya `pdwSize` da null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="395d7-116">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="395d7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="395d7-117">Remarks</span></span>  

 <span data-ttu-id="395d7-118">Başarıyla tamamlandığında `pdwSize` bağımsız değişkeni yol dizesinin uzunluğuna ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="395d7-118">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="395d7-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="395d7-119">Requirements</span></span>  

 <span data-ttu-id="395d7-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="395d7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="395d7-121">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="395d7-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="395d7-122">**Kitaplık:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="395d7-122">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="395d7-123">Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="395d7-123">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="395d7-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="395d7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395d7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="395d7-125">See also</span></span>

- [<span data-ttu-id="395d7-126">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="395d7-126">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="395d7-127">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="395d7-127">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="395d7-128">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="395d7-128">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
