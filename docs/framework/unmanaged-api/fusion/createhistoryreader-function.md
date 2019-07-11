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
ms.openlocfilehash: ee30d4f32e05fab27ae70052b28d3d152594cf90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778419"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="b0519-102">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="b0519-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="b0519-103">Belirtilen dosya için geçmiş okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0519-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0519-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0519-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0519-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0519-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="b0519-106">[in] Dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="b0519-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="b0519-107">[out] Başarıyla tamamlandığında, geçmiş Okuyucu için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="b0519-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0519-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b0519-108">Return Value</span></span>  
 <span data-ttu-id="b0519-109">Bu yöntem, aşağıdaki tabloda açıklanan değerlere ek olarak Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b0519-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="b0519-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="b0519-110">Return code</span></span>|<span data-ttu-id="b0519-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0519-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b0519-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0519-112">S_OK</span></span>|<span data-ttu-id="b0519-113">Yöntemi başarıyla tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0519-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="b0519-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b0519-114">E_INVALIDARG</span></span>|<span data-ttu-id="b0519-115">Bildiren `wzFilePath` veya `ppHistoryReader` null bir başvuru ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b0519-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0519-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0519-116">Requirements</span></span>  
 <span data-ttu-id="b0519-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0519-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0519-118">**Kitaplığı:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="b0519-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="b0519-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0519-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0519-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0519-120">See also</span></span>

- [<span data-ttu-id="b0519-121">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b0519-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
