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
ms.openlocfilehash: 64d76efa8c2f29fda559e5c84217b865540027ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175830"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="aa7f2-102">IMetaDataEmit::DefineMethodImpl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa7f2-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="aa7f2-103">Arabirimden devralınan bir yöntemin uygulanması için bir tanım oluşturur ve bu yöntem-uygulama tanımına bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa7f2-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa7f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa7f2-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa7f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa7f2-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="aa7f2-106">[içinde] Uygulama `mdTypedef` sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="aa7f2-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="aa7f2-107">[içinde] Kod `mdMethodDef` `mdMemberRef` gövdesinin belirteci.</span><span class="sxs-lookup"><span data-stu-id="aa7f2-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="aa7f2-108">[içinde] Uygulanan `mdMethodDef` `mdMemberRef` arabirim yönteminin belirteci.</span><span class="sxs-lookup"><span data-stu-id="aa7f2-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa7f2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa7f2-109">Requirements</span></span>  
 <span data-ttu-id="aa7f2-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa7f2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa7f2-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa7f2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa7f2-112">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="aa7f2-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa7f2-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa7f2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7f2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa7f2-114">See also</span></span>

- [<span data-ttu-id="aa7f2-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa7f2-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="aa7f2-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa7f2-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
