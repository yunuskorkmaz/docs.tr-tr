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
ms.openlocfilehash: a87d18b15f858b608d99a511ed9bdad73fd2b251
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493686"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="c1584-102">IMetaDataEmit::DefineModuleRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1584-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="c1584-103">Belirtilen ada sahip bir modül meta veri imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1584-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1584-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1584-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1584-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1584-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="c1584-106">[in] Diğer meta veri dosyası genellikle bir DLL'nin adı.</span><span class="sxs-lookup"><span data-stu-id="c1584-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="c1584-107">Yalnızca dosya adını budur.</span><span class="sxs-lookup"><span data-stu-id="c1584-107">This is the file name only.</span></span> <span data-ttu-id="c1584-108">Bir tam yol adını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c1584-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="c1584-109">[out] Atanan `mdModuleRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="c1584-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1584-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1584-110">Requirements</span></span>  
 <span data-ttu-id="c1584-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1584-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1584-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c1584-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1584-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="c1584-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1584-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1584-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1584-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1584-115">See also</span></span>
- [<span data-ttu-id="c1584-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1584-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c1584-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1584-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
