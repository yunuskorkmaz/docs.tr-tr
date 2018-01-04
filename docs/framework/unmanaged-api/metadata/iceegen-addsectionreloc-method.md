---
title: "ICeeGen::AddSectionReloc Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AddSectionReloc
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e4bb3b1e436f51726ce50f80e1fd88c10f20fd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="424c4-102">ICeeGen::AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="424c4-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="424c4-103">.Reloc yönerge kodu Bankası'na ekler.</span><span class="sxs-lookup"><span data-stu-id="424c4-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="424c4-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="424c4-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="424c4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="424c4-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="424c4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="424c4-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="424c4-107">[in] Bellek içi kodun bir .reloc yönergesi eklenecek bölümü.</span><span class="sxs-lookup"><span data-stu-id="424c4-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="424c4-108">[in] Bölüm uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="424c4-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="424c4-109">[in] Bölümüne `offset` başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="424c4-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="424c4-110">[in] Aşağıdakilerden birini [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) eklemek için .reloc yönerge türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="424c4-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="424c4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="424c4-111">Requirements</span></span>  
 <span data-ttu-id="424c4-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="424c4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="424c4-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="424c4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="424c4-114">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="424c4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="424c4-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="424c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="424c4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="424c4-116">See Also</span></span>  
 [<span data-ttu-id="424c4-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="424c4-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
