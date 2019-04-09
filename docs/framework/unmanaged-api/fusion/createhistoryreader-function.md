---
title: CreateHistoryReader İşlevi
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e438006d6424866514e73119c05e8fd69d7ba62e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132268"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="99912-102">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="99912-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="99912-103">Belirtilen dosya için geçmiş okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99912-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99912-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99912-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="99912-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99912-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="99912-106">[in] Dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="99912-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="99912-107">[out] Başarıyla tamamlandığında, geçmiş Okuyucu için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="99912-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99912-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99912-108">Return Value</span></span>  
 <span data-ttu-id="99912-109">Bu yöntem, aşağıdaki tabloda açıklanan değerlere ek olarak Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="99912-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="99912-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="99912-110">Return code</span></span>|<span data-ttu-id="99912-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99912-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="99912-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="99912-112">S_OK</span></span>|<span data-ttu-id="99912-113">Yöntemi başarıyla tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99912-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="99912-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="99912-114">E_INVALIDARG</span></span>|<span data-ttu-id="99912-115">Bildiren `wzFilePath` veya `ppHistoryReader` null bir başvuru ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="99912-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99912-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99912-116">Requirements</span></span>  
 <span data-ttu-id="99912-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99912-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99912-118">**Kitaplığı:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="99912-118">**Library:** Fusion.dll</span></span>  
  
 **<span data-ttu-id="99912-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="99912-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99912-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99912-120">See also</span></span>

- [<span data-ttu-id="99912-121">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="99912-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
