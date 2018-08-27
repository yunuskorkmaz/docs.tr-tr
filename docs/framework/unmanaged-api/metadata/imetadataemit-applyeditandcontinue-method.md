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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: faa9bc412e67e0e49ee969bd8b246a424fe628a0
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930943"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="708b5-102">IMetaDataEmit::ApplyEditAndContinue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="708b5-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="708b5-103">Belirtilen meta verilerde yapılan değişiklikleri geçerli derleme kapsamı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="708b5-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="708b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="708b5-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="708b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="708b5-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="708b5-106">\[içinde\] işaretçi bir [IUnknown](/cpp/atl/iunknown) taşınabilir yürütülebilir (PE) dosyasından delta meta verileri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="708b5-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="708b5-107">Delta meta veriler modülün gerçek meta verilerinin kopyaya yapılan değişiklikler içeren bloğudur.</span><span class="sxs-lookup"><span data-stu-id="708b5-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="708b5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="708b5-108">Requirements</span></span>  
 <span data-ttu-id="708b5-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="708b5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="708b5-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="708b5-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="708b5-111">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılan</span><span class="sxs-lookup"><span data-stu-id="708b5-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="708b5-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="708b5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708b5-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="708b5-113">See Also</span></span>  
 [<span data-ttu-id="708b5-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="708b5-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="708b5-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="708b5-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
