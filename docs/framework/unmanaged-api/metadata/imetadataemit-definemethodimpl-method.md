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
ms.openlocfilehash: 5ed5afbbf49b6680d00e78b6af3d45c6f0a7229d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004497"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="13891-102">IMetaDataEmit::DefineMethodImpl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13891-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="13891-103">Bir arabirimden devralınan yöntemin uygulanması için bir tanım oluşturur ve bu yöntem uygulama tanımına bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="13891-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13891-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13891-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13891-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13891-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="13891-106">'ndaki `mdTypedef`Uygulama sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="13891-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="13891-107">'ndaki `mdMethodDef` `mdMemberRef` Kod gövdesinin veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="13891-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="13891-108">'ndaki `mdMethodDef` `mdMemberRef` Uygulanan arabirim yönteminin veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="13891-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13891-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13891-109">Requirements</span></span>  
 <span data-ttu-id="13891-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13891-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13891-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="13891-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13891-112">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="13891-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13891-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13891-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13891-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13891-114">See also</span></span>

- [<span data-ttu-id="13891-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13891-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="13891-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13891-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
