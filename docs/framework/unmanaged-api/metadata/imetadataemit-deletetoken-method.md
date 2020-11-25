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
ms.openlocfilehash: eaa465855c9e933286bcdd189e62048510088ec7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722082"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="bd644-102">IMetaDataEmit::DeleteToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd644-102">IMetaDataEmit::DeleteToken Method</span></span>

<span data-ttu-id="bd644-103">Belirtilen belirteci geçerli meta veri kapsamından siler.</span><span class="sxs-lookup"><span data-stu-id="bd644-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd644-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bd644-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd644-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd644-105">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="bd644-106">'ndaki Silinecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="bd644-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd644-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd644-107">Requirements</span></span>  

 <span data-ttu-id="bd644-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd644-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd644-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bd644-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd644-110">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="bd644-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd644-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd644-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd644-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd644-112">See also</span></span>

- [<span data-ttu-id="bd644-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd644-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="bd644-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd644-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
