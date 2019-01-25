---
title: IMetaDataImport::GetModuleFromScope Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 931b17858465d4ff380069fc2cf2bb37cb7a7ffc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718188"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="6c545-102">IMetaDataImport::GetModuleFromScope Metodu</span><span class="sxs-lookup"><span data-stu-id="6c545-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="6c545-103">Bir meta veri geçerli meta veri kapsamda başvuru modülü için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="6c545-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c545-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c545-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c545-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c545-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="6c545-106">[out] Geçerli meta veri kapsamda başvurulan modülü temsil eden belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c545-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c545-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c545-107">Requirements</span></span>  
 <span data-ttu-id="6c545-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c545-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c545-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6c545-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c545-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6c545-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c545-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c545-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c545-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c545-112">See also</span></span>
- [<span data-ttu-id="6c545-113">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c545-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6c545-114">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c545-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
