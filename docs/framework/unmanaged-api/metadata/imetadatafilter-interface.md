---
title: IMetaDataFilter Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e1975a5063217299ddbcdce6f625d5a1285d5b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642561"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="a0e6f-102">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0e6f-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="a0e6f-103">İşaretleme ve meta veri belirteçleri zaten alınmış eylemleri tekrarlamayı önlemek üzere filtreleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0e6f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a0e6f-104">Methods</span></span>  
  
|<span data-ttu-id="a0e6f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a0e6f-105">Method</span></span>|<span data-ttu-id="a0e6f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0e6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0e6f-107">IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0e6f-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="a0e6f-108">Belirtilen meta veri belirteci işlenen olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="a0e6f-109">MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0e6f-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="a0e6f-110">Belirtilen meta veri belirteci işlendiğini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="a0e6f-111">UnmarkAll Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0e6f-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="a0e6f-112">Geçerli meta veri kapsamdaki tüm belirteçlerin işleme işaretleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0e6f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0e6f-113">Requirements</span></span>  
 <span data-ttu-id="a0e6f-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0e6f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e6f-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a0e6f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0e6f-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="a0e6f-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0e6f-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e6f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e6f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0e6f-118">See also</span></span>
- [<span data-ttu-id="a0e6f-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a0e6f-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
