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
ms.openlocfilehash: f1f8acc546c0d96aca079223200b43aec933f729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447915"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="2de2a-102">IMetaDataImport::GetModuleFromScope Metodu</span><span class="sxs-lookup"><span data-stu-id="2de2a-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="2de2a-103">Bir meta veri geçerli meta veri kapsamda başvurulan modül belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="2de2a-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2de2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2de2a-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2de2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2de2a-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="2de2a-106">[out] Geçerli meta veri kapsamda başvurulan modülü temsil eden belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2de2a-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2de2a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2de2a-107">Requirements</span></span>  
 <span data-ttu-id="2de2a-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2de2a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2de2a-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2de2a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2de2a-110">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2de2a-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2de2a-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2de2a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de2a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2de2a-112">See Also</span></span>  
 [<span data-ttu-id="2de2a-113">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2de2a-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2de2a-114">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2de2a-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
