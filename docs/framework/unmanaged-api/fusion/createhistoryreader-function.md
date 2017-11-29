---
title: "CreateHistoryReader İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateHistoryReader
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateHistoryReader
helpviewer_keywords: CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f4b09f592a27b7d3d25b2dbe13be7e261023bf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="5fc25-102">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="5fc25-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="5fc25-103">Belirtilen dosya için bir geçmiş okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5fc25-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fc25-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fc25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fc25-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="5fc25-106">[in] Dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="5fc25-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="5fc25-107">[out] Başarılı tamamlanma, geçmiş Okuyucu için bir işaretçi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5fc25-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fc25-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5fc25-108">Return Value</span></span>  
 <span data-ttu-id="5fc25-109">Bu yöntem, ek olarak aşağıdaki tabloda açıklanan değerleri Winerror.h'de içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5fc25-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="5fc25-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="5fc25-110">Return code</span></span>|<span data-ttu-id="5fc25-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fc25-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5fc25-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5fc25-112">S_OK</span></span>|<span data-ttu-id="5fc25-113">Yöntem başarıyla tamamlanıp tamamlanmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fc25-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="5fc25-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5fc25-114">E_INVALIDARG</span></span>|<span data-ttu-id="5fc25-115">Belirten `wzFilePath` veya `ppHistoryReader` null bir başvuru ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5fc25-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fc25-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fc25-116">Requirements</span></span>  
 <span data-ttu-id="5fc25-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fc25-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fc25-118">**Kitaplığı:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="5fc25-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="5fc25-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fc25-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc25-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fc25-120">See Also</span></span>  
 [<span data-ttu-id="5fc25-121">Fusion genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="5fc25-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
