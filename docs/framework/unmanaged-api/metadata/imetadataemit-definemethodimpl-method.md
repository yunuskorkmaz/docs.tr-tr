---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D Efinemethodımpl yöntemi'
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
ms.openlocfilehash: 9c79d713e61bfcc7b3191e570ed727b128422bf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753412"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="09f93-103">IMetaDataEmit::DefineMethodImpl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09f93-103">IMetaDataEmit::DefineMethodImpl Method</span></span>

<span data-ttu-id="09f93-104">Bir arabirimden devralınan yöntemin uygulanması için bir tanım oluşturur ve bu yöntem uygulama tanımına bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="09f93-104">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f93-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09f93-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09f93-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09f93-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="09f93-107">'ndaki `mdTypedef` Uygulama sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="09f93-107">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="09f93-108">'ndaki `mdMethodDef` `mdMemberRef` Kod gövdesinin veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="09f93-108">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="09f93-109">'ndaki `mdMethodDef` `mdMemberRef` Uygulanan arabirim yönteminin veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="09f93-109">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09f93-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09f93-110">Requirements</span></span>  

 <span data-ttu-id="09f93-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09f93-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09f93-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="09f93-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09f93-113">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="09f93-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09f93-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09f93-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f93-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09f93-115">See also</span></span>

- [<span data-ttu-id="09f93-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09f93-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="09f93-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09f93-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
