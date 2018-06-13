---
title: IMetaDataEmit::DefineModuleRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4503c3c745fde148c77ff30c9ece008dd9d54829
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445802"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="69063-102">IMetaDataEmit::DefineModuleRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69063-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="69063-103">Belirtilen ada sahip bir modül için meta verileri imza oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69063-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69063-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69063-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69063-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69063-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="69063-106">[in] Diğer meta veri dosyası genellikle bir DLL adı.</span><span class="sxs-lookup"><span data-stu-id="69063-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="69063-107">Bu yalnızca dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="69063-107">This is the file name only.</span></span> <span data-ttu-id="69063-108">Bir tam yol adını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="69063-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="69063-109">[out] Atanan `mdModuleRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="69063-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69063-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69063-110">Requirements</span></span>  
 <span data-ttu-id="69063-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69063-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69063-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="69063-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69063-113">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="69063-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69063-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69063-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69063-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69063-115">See Also</span></span>  
 [<span data-ttu-id="69063-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69063-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="69063-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69063-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
