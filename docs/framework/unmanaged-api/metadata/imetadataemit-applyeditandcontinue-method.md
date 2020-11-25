---
title: IMetaDataEmit::ApplyEditAndContinue Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: 0cc84893c4937bf6b23eae0d63b92b3b871901dd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700580"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="bdbed-102">IMetaDataEmit::ApplyEditAndContinue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdbed-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>

<span data-ttu-id="bdbed-103">Geçerli derleme kapsamını belirtilen meta verilerde yapılan değişikliklerle güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="bdbed-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdbed-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bdbed-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdbed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bdbed-105">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="bdbed-106">\[\]Taşınabilir çalıştırılabilir (PE) dosyasındaki Delta meta verilerini temsil eden bir [IUnknown](/cpp/atl/iunknown) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bdbed-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="bdbed-107">Delta meta verileri, modülün gerçek meta verilerinin kopyasında yapılan değişiklikleri içeren meta veri bloğudur.</span><span class="sxs-lookup"><span data-stu-id="bdbed-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdbed-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdbed-108">Requirements</span></span>  

 <span data-ttu-id="bdbed-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdbed-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdbed-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bdbed-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bdbed-111">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="bdbed-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bdbed-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdbed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdbed-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdbed-113">See also</span></span>

- [<span data-ttu-id="bdbed-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bdbed-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="bdbed-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bdbed-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
