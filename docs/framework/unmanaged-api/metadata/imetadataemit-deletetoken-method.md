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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138248"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="ccde9-102">IMetaDataEmit::DeleteToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ccde9-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="ccde9-103">Belirtilen belirteç geçerli bir meta veri kapsamından siler.</span><span class="sxs-lookup"><span data-stu-id="ccde9-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccde9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccde9-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccde9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccde9-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="ccde9-106">[in] Silinecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="ccde9-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccde9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccde9-107">Requirements</span></span>  
 <span data-ttu-id="ccde9-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccde9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccde9-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ccde9-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccde9-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ccde9-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ccde9-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ccde9-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ccde9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccde9-112">See also</span></span>

- [<span data-ttu-id="ccde9-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccde9-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ccde9-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccde9-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
