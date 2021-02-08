---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D eleteToken yöntemi'
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
ms.openlocfilehash: 5c28b56b06f994057409ef8fa17179cb0b0e205b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783956"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="49f6a-103">IMetaDataEmit::DeleteToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49f6a-103">IMetaDataEmit::DeleteToken Method</span></span>

<span data-ttu-id="49f6a-104">Belirtilen belirteci geçerli meta veri kapsamından siler.</span><span class="sxs-lookup"><span data-stu-id="49f6a-104">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49f6a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49f6a-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49f6a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49f6a-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="49f6a-107">'ndaki Silinecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="49f6a-107">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49f6a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49f6a-108">Requirements</span></span>  

 <span data-ttu-id="49f6a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49f6a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49f6a-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="49f6a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49f6a-111">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="49f6a-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49f6a-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49f6a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49f6a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49f6a-113">See also</span></span>

- [<span data-ttu-id="49f6a-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49f6a-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="49f6a-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49f6a-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
