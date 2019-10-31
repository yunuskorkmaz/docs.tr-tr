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
ms.openlocfilehash: 80979f0424469bb1d4771ad6507bb8c9d5364ab4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108603"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="63233-102">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="63233-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="63233-103">Belirtilen dosya için bir geçmiş okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63233-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63233-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63233-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="63233-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63233-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="63233-106">'ndaki Dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="63233-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="63233-107">dışı Başarılı tamamlandığında, geçmiş okuyucu için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="63233-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63233-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63233-108">Return Value</span></span>  
 <span data-ttu-id="63233-109">Bu yöntem, aşağıdaki tabloda açıklanan değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="63233-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="63233-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="63233-110">Return code</span></span>|<span data-ttu-id="63233-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63233-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="63233-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="63233-112">S_OK</span></span>|<span data-ttu-id="63233-113">Metodun başarıyla tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63233-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="63233-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="63233-114">E_INVALIDARG</span></span>|<span data-ttu-id="63233-115">`wzFilePath` veya `ppHistoryReader` null başvuruya ayarlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63233-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63233-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63233-116">Requirements</span></span>  
 <span data-ttu-id="63233-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63233-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63233-118">**Kitaplık:** Fusion. dll</span><span class="sxs-lookup"><span data-stu-id="63233-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="63233-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63233-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63233-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63233-120">See also</span></span>

- [<span data-ttu-id="63233-121">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="63233-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
