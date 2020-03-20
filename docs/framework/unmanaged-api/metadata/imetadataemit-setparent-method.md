---
title: IMetaDataEmit::SetParent Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: 7389e9233fd946cdb2c810bec01cfbfffc8b707d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175609"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="30b26-102">IMetaDataEmit::SetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30b26-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="30b26-103">Belirtilen üye, iMetaDataEmit bir önceki çağrı ile [tanımlanan::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), belirtilen tür üyesi olduğunu kurar, iMetaDataEmit bir önceki çağrı ile [tanımlanan::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="30b26-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30b26-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30b26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30b26-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="30b26-106">[içinde] Yeni `mdMemberRef` bir ebeveyn almak için belirteç.</span><span class="sxs-lookup"><span data-stu-id="30b26-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="30b26-107">[içinde] Yeni `mdToken` ebeveyn için.</span><span class="sxs-lookup"><span data-stu-id="30b26-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b26-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30b26-108">Requirements</span></span>  
 <span data-ttu-id="30b26-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30b26-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b26-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="30b26-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30b26-111">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="30b26-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30b26-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b26-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b26-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30b26-113">See also</span></span>

- [<span data-ttu-id="30b26-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30b26-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="30b26-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30b26-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
