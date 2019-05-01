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
ms.openlocfilehash: 6969f2c1df9b5b04122ed6aef550697171123cf5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992504"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="9f885-102">IMetaDataFilter::IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f885-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="9f885-103">Belirtilen meta veri belirteci işlendi olarak işaretlenmiş olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="9f885-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f885-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f885-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f885-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f885-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9f885-106">[in] İşleme işareti incelemek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="9f885-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="9f885-107">[out] Bir değer `true` varsa `tk` işlenen; Aksi takdirde olmuştur `false`.</span><span class="sxs-lookup"><span data-stu-id="9f885-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f885-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f885-108">Requirements</span></span>  
 <span data-ttu-id="9f885-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f885-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f885-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9f885-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f885-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="9f885-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f885-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f885-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f885-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f885-113">See also</span></span>

- [<span data-ttu-id="9f885-114">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f885-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
