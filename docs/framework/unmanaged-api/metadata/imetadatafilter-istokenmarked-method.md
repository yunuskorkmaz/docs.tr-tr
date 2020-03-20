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
ms.openlocfilehash: 47377e892aaf2bdd96a297630c47fe52215b0564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177390"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="20edd-102">IMetaDataFilter::IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20edd-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="20edd-103">Belirtilen meta veri belirteci işlenmiş olarak işaretlenmiş olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="20edd-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20edd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20edd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20edd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20edd-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="20edd-106">[içinde] İşlem işareti için incelenmek üzere belirteç.</span><span class="sxs-lookup"><span data-stu-id="20edd-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="20edd-107">[çıkış] İşlenmiş `true` sayılsa `tk` değeri; aksi `false`takdirde .</span><span class="sxs-lookup"><span data-stu-id="20edd-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20edd-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20edd-108">Requirements</span></span>  
 <span data-ttu-id="20edd-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20edd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20edd-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="20edd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20edd-111">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="20edd-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="20edd-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20edd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20edd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20edd-113">See also</span></span>

- [<span data-ttu-id="20edd-114">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20edd-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
