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
ms.openlocfilehash: 484adf288356b9955fe0cac0bb30002ec1f012d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724444"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="b7dff-102">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="b7dff-102">GetHistoryFileDirectory Function</span></span>

<span data-ttu-id="b7dff-103">Uygulama geçmişi dizininin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="b7dff-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7dff-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b7dff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7dff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7dff-105">Parameters</span></span>  

 `wzDir`  
 <span data-ttu-id="b7dff-106">dışı Uygulama geçmişi dizininin yolunu tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="b7dff-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="b7dff-107">[in, out] Arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b7dff-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7dff-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b7dff-108">Return Value</span></span>  

 <span data-ttu-id="b7dff-109">Bu yöntem, aşağıdaki değerlere ek olarak WinError. h dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7dff-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="b7dff-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="b7dff-110">Return code</span></span>|<span data-ttu-id="b7dff-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7dff-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b7dff-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7dff-112">S_OK</span></span>|<span data-ttu-id="b7dff-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b7dff-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="b7dff-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b7dff-114">E_INVALIDARG</span></span>|<span data-ttu-id="b7dff-115">`wzDir` ya `pdwSize` da null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="b7dff-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7dff-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7dff-116">Remarks</span></span>  

 <span data-ttu-id="b7dff-117">Başarıyla tamamlandığında `pdwSize` bağımsız değişkeni yol dizesinin uzunluğuna ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b7dff-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7dff-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7dff-118">Requirements</span></span>  

 <span data-ttu-id="b7dff-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7dff-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7dff-120">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b7dff-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b7dff-121">**Kitaplık:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="b7dff-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="b7dff-122">Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7dff-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b7dff-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7dff-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7dff-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7dff-124">See also</span></span>

- [<span data-ttu-id="b7dff-125">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="b7dff-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="b7dff-126">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="b7dff-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="b7dff-127">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b7dff-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
