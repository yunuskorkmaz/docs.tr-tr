---
description: ': IMetaDataFilter:: ıstokenişaretlenen yöntem hakkında daha fazla bilgi'
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
ms.openlocfilehash: dddb0aa9040a2f5ef3ec972bb37a9e8778ddffe8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677796"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="0862a-103">IMetaDataFilter::IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0862a-103">IMetaDataFilter::IsTokenMarked Method</span></span>

<span data-ttu-id="0862a-104">Belirtilen meta veri belirtecinin işlenmiş olarak işaretlenip işaretlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="0862a-104">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0862a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0862a-105">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0862a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0862a-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="0862a-107">'ndaki Bir işleme işareti için incelenecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="0862a-107">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="0862a-108">dışı İşlendiği bir değer `true` `tk` ; Aksi takdirde `false` .</span><span class="sxs-lookup"><span data-stu-id="0862a-108">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0862a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0862a-109">Requirements</span></span>  

 <span data-ttu-id="0862a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0862a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0862a-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0862a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0862a-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0862a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0862a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0862a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0862a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0862a-114">See also</span></span>

- [<span data-ttu-id="0862a-115">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0862a-115">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
