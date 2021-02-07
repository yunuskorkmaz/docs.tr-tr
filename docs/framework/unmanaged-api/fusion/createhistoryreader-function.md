---
description: 'Daha fazla bilgi edinin: Creategeçmişini okuyucu Işlevi'
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
ms.openlocfilehash: 0943f3d0f3322d34ed92c0a96b909e4d63ec5e7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761128"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="faeac-103">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="faeac-103">CreateHistoryReader Function</span></span>

<span data-ttu-id="faeac-104">Belirtilen dosya için bir geçmiş okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="faeac-104">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faeac-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="faeac-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="faeac-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="faeac-106">Parameters</span></span>  

 `wzFilePath`  
 <span data-ttu-id="faeac-107">'ndaki Dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="faeac-107">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="faeac-108">dışı Başarılı tamamlandığında, geçmiş okuyucu için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="faeac-108">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faeac-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="faeac-109">Return Value</span></span>  

 <span data-ttu-id="faeac-110">Bu yöntem, aşağıdaki tabloda açıklanan değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="faeac-110">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="faeac-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="faeac-111">Return code</span></span>|<span data-ttu-id="faeac-112">Description</span><span class="sxs-lookup"><span data-stu-id="faeac-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="faeac-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="faeac-113">S_OK</span></span>|<span data-ttu-id="faeac-114">Metodun başarıyla tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="faeac-114">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="faeac-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="faeac-115">E_INVALIDARG</span></span>|<span data-ttu-id="faeac-116">`wzFilePath`Bunun veya `ppHistoryReader` null bir başvuruya ayarlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="faeac-116">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="faeac-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faeac-117">Requirements</span></span>  

 <span data-ttu-id="faeac-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faeac-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faeac-119">**Kitaplık:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="faeac-119">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="faeac-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faeac-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faeac-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faeac-121">See also</span></span>

- [<span data-ttu-id="faeac-122">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="faeac-122">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
