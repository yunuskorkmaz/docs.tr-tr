---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma:: ApplyEditAndContinue yöntemi'
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
ms.openlocfilehash: 46454c4141aa220b43820307c86765a1827251df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753503"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="9961d-103">IMetaDataEmit::ApplyEditAndContinue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9961d-103">IMetaDataEmit::ApplyEditAndContinue Method</span></span>

<span data-ttu-id="9961d-104">Geçerli derleme kapsamını belirtilen meta verilerde yapılan değişikliklerle güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9961d-104">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9961d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9961d-105">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9961d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9961d-106">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="9961d-107">\[\]Taşınabilir çalıştırılabilir (PE) dosyasındaki Delta meta verilerini temsil eden bir [IUnknown](/cpp/atl/iunknown) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9961d-107">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="9961d-108">Delta meta verileri, modülün gerçek meta verilerinin kopyasında yapılan değişiklikleri içeren meta veri bloğudur.</span><span class="sxs-lookup"><span data-stu-id="9961d-108">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9961d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9961d-109">Requirements</span></span>  

 <span data-ttu-id="9961d-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9961d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9961d-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9961d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9961d-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9961d-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9961d-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9961d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9961d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9961d-114">See also</span></span>

- [<span data-ttu-id="9961d-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9961d-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9961d-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9961d-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
