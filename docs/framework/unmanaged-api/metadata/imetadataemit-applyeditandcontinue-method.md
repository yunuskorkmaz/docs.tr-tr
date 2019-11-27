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
ms.openlocfilehash: b9cad4c9647983e5b39f9b7a5d03736f2848e1c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432689"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="77289-102">IMetaDataEmit::ApplyEditAndContinue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77289-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="77289-103">Geçerli derleme kapsamını belirtilen meta verilerde yapılan değişikliklerle güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="77289-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77289-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77289-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77289-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77289-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="77289-106">Taşınabilir çalıştırılabilir (PE) dosyasındaki Delta meta verilerini temsil eden bir [IUnknown](/cpp/atl/iunknown) nesnesine\] işaretçisinde \[.</span><span class="sxs-lookup"><span data-stu-id="77289-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="77289-107">Delta meta verileri, modülün gerçek meta verilerinin kopyasında yapılan değişiklikleri içeren meta veri bloğudur.</span><span class="sxs-lookup"><span data-stu-id="77289-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77289-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77289-108">Requirements</span></span>  
 <span data-ttu-id="77289-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77289-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77289-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="77289-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77289-111">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="77289-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77289-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77289-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77289-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77289-113">See also</span></span>

- [<span data-ttu-id="77289-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77289-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="77289-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77289-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
