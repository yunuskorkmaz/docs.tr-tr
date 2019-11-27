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
ms.openlocfilehash: 99f529a151a42cf4a9ee1f74bd3a76a5b6b1b35f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445267"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="d1a7d-102">IMetaDataEmit::DefineMethodImpl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1a7d-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="d1a7d-103">Bir arabirimden devralınan yöntemin uygulanması için bir tanım oluşturur ve bu yöntem uygulama tanımına bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1a7d-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1a7d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1a7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1a7d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d1a7d-106">'ndaki Uygulama sınıfının `mdTypedef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="d1a7d-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="d1a7d-107">'ndaki Kod gövdesinin `mdMethodDef` veya `mdMemberRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="d1a7d-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="d1a7d-108">'ndaki Uygulanan arabirim yönteminin `mdMethodDef` veya `mdMemberRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="d1a7d-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1a7d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1a7d-109">Requirements</span></span>  
 <span data-ttu-id="d1a7d-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1a7d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1a7d-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1a7d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1a7d-112">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d1a7d-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1a7d-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1a7d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a7d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1a7d-114">See also</span></span>

- [<span data-ttu-id="d1a7d-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1a7d-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d1a7d-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1a7d-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
