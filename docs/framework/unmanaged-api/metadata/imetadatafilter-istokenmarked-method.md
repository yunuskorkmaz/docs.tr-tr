---
title: IMetaDataFilter::IsTokenMarked Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e15f4e8691db13b9a646a1e1d783075acfcdd896
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777085"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="60c49-102">IMetaDataFilter::IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60c49-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="60c49-103">Belirtilen meta veri belirteci işlendi olarak işaretlenmiş olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="60c49-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60c49-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60c49-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60c49-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="60c49-106">[in] İşleme işareti incelemek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="60c49-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="60c49-107">[out] Bir değer `true` varsa `tk` işlenen; Aksi takdirde olmuştur `false`.</span><span class="sxs-lookup"><span data-stu-id="60c49-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60c49-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60c49-108">Requirements</span></span>  
 <span data-ttu-id="60c49-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60c49-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c49-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="60c49-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60c49-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="60c49-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60c49-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c49-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c49-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60c49-113">See also</span></span>

- [<span data-ttu-id="60c49-114">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60c49-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
