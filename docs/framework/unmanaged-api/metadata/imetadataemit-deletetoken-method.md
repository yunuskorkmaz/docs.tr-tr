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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d85fb62936678f830ca7eaf26a97c36be5f23ac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050096"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="5c142-102">IMetaDataEmit::DeleteToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c142-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="5c142-103">Belirtilen belirteç geçerli bir meta veri kapsamından siler.</span><span class="sxs-lookup"><span data-stu-id="5c142-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c142-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c142-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c142-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c142-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="5c142-106">[in] Silinecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="5c142-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c142-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c142-107">Requirements</span></span>  
 <span data-ttu-id="5c142-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c142-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c142-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5c142-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c142-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="5c142-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c142-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c142-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c142-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c142-112">See also</span></span>

- [<span data-ttu-id="5c142-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c142-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5c142-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c142-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
