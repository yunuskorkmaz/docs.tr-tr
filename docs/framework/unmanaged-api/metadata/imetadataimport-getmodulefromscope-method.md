---
title: IMetaDataImport::GetModuleFromScope Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleFromScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d7a9987f9a557cda79483e46c1798d471aa13944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="f1916-102">IMetaDataImport::GetModuleFromScope Metodu</span><span class="sxs-lookup"><span data-stu-id="f1916-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="f1916-103">Bir meta veri geçerli meta veri kapsamda başvurulan modül belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="f1916-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1916-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1916-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1916-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1916-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="f1916-106">[out] Geçerli meta veri kapsamda başvurulan modülü temsil eden belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1916-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1916-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1916-107">Requirements</span></span>  
 <span data-ttu-id="f1916-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1916-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1916-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1916-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1916-110">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f1916-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1916-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1916-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1916-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1916-112">See Also</span></span>  
 [<span data-ttu-id="f1916-113">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1916-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f1916-114">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1916-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
