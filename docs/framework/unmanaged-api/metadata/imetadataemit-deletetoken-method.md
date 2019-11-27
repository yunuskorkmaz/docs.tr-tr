---
title: IMetaDataEmit::DeleteToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: e8c145632911817e8e19d587bb8afead0a6c33af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434340"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="cf9a7-102">IMetaDataEmit::DeleteToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf9a7-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="cf9a7-103">Belirtilen belirteci geçerli meta veri kapsamından siler.</span><span class="sxs-lookup"><span data-stu-id="cf9a7-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf9a7-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf9a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf9a7-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="cf9a7-106">'ndaki Silinecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="cf9a7-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf9a7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf9a7-107">Requirements</span></span>  
 <span data-ttu-id="cf9a7-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf9a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf9a7-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cf9a7-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf9a7-110">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cf9a7-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf9a7-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf9a7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9a7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf9a7-112">See also</span></span>

- [<span data-ttu-id="cf9a7-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf9a7-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cf9a7-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf9a7-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
