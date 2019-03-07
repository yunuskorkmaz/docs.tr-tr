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
ms.openlocfilehash: b7d831038221870fc54cdfc65230bca6dd42f867
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485713"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="572d6-102">IMetaDataFilter::IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="572d6-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="572d6-103">Belirtilen meta veri belirteci işlendi olarak işaretlenmiş olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="572d6-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="572d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="572d6-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="572d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="572d6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="572d6-106">[in] İşleme işareti incelemek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="572d6-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="572d6-107">[out] Bir değer `true` varsa `tk` işlenen; Aksi takdirde olmuştur `false`.</span><span class="sxs-lookup"><span data-stu-id="572d6-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="572d6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="572d6-108">Requirements</span></span>  
 <span data-ttu-id="572d6-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="572d6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="572d6-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="572d6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="572d6-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="572d6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="572d6-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="572d6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572d6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="572d6-113">See also</span></span>
- [<span data-ttu-id="572d6-114">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="572d6-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
