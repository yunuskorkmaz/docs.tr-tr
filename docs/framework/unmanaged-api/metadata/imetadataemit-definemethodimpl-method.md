---
title: IMetaDataEmit::DefineMethodImpl Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 184ae0aee6947aa686e80541ab3ba36e0f4e1647
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424008"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="75046-102">IMetaDataEmit::DefineMethodImpl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75046-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="75046-103">Bir arabirimden devralınan bir yöntemi uygulaması için bir tanım oluşturur ve bu yöntem uygulaması tanımı için bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="75046-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75046-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75046-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75046-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75046-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="75046-106">[in] `mdTypedef` Uygulayan sınıfın belirteci.</span><span class="sxs-lookup"><span data-stu-id="75046-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="75046-107">[in] `mdMethodDef` Veya `mdMemberRef` kod gövde belirteci.</span><span class="sxs-lookup"><span data-stu-id="75046-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="75046-108">[in] `mdMethodDef` Veya `mdMemberRef` uygulanan arabirim yönteminin belirteci.</span><span class="sxs-lookup"><span data-stu-id="75046-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75046-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75046-109">Requirements</span></span>  
 <span data-ttu-id="75046-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75046-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75046-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="75046-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75046-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="75046-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75046-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75046-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75046-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75046-114">See also</span></span>

- [<span data-ttu-id="75046-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75046-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="75046-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75046-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
