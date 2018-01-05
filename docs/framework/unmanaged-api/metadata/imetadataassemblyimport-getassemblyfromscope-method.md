---
title: IMetaDataAssemblyImport::GetAssemblyFromScope Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyFromScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 725e442180da16ae8165cbea2f625178eb943354
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="59b12-102">IMetaDataAssemblyImport::GetAssemblyFromScope Metodu</span><span class="sxs-lookup"><span data-stu-id="59b12-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="59b12-103">Bir işaretçi derlemeye geçerli kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="59b12-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59b12-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59b12-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59b12-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="59b12-106">[out] Bir işaretçi alınan `mdAssembly` derleme tanımlayan belirteci.</span><span class="sxs-lookup"><span data-stu-id="59b12-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59b12-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59b12-107">Requirements</span></span>  
 <span data-ttu-id="59b12-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59b12-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59b12-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="59b12-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59b12-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="59b12-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59b12-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59b12-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b12-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59b12-112">See Also</span></span>  
 [<span data-ttu-id="59b12-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59b12-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
