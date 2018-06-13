---
title: IMetaDataEmit::SetModuleProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce8be38f6e146b2a8669ea5c694353615f6f2d66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445909"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="ad587-102">IMetaDataEmit::SetModuleProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad587-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="ad587-103">Güncelleştirmeler için önceki bir çağrı tarafından tanımlanan bir modül başvurular [Imetadataemit::definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="ad587-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad587-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad587-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad587-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad587-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ad587-106">[in] Unicode modülü adı.</span><span class="sxs-lookup"><span data-stu-id="ad587-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="ad587-107">Yalnızca dosya adını ve tam yol adı budur.</span><span class="sxs-lookup"><span data-stu-id="ad587-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad587-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad587-108">Requirements</span></span>  
 <span data-ttu-id="ad587-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad587-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad587-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad587-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad587-111">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ad587-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad587-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad587-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad587-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad587-113">See Also</span></span>  
 [<span data-ttu-id="ad587-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad587-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ad587-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad587-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
