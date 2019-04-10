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
ms.openlocfilehash: c18c72ecbaf2e0d3153ad7f00caf73421e35fa0a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225319"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="828a1-102">IMetaDataEmit::ApplyEditAndContinue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="828a1-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="828a1-103">Belirtilen meta verilerde yapılan değişiklikleri geçerli derleme kapsamı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="828a1-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="828a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="828a1-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="828a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="828a1-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="828a1-106">\[içinde\] işaretçi bir [IUnknown](/cpp/atl/iunknown) taşınabilir yürütülebilir (PE) dosyasından delta meta verileri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="828a1-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="828a1-107">Delta meta veriler modülün gerçek meta verilerinin kopyaya yapılan değişiklikler içeren bloğudur.</span><span class="sxs-lookup"><span data-stu-id="828a1-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="828a1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="828a1-108">Requirements</span></span>  
 <span data-ttu-id="828a1-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="828a1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="828a1-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="828a1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="828a1-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="828a1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="828a1-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="828a1-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="828a1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="828a1-113">See also</span></span>

- [<span data-ttu-id="828a1-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="828a1-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="828a1-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="828a1-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
