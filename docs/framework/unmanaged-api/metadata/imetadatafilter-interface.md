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
ms.openlocfilehash: e8b15f478eb3b94b7cdcab3b69d54e7cc99be13b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440171"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="0a8a8-102">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a8a8-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="0a8a8-103">Zaten alınmış olan işlemleri önlemek için meta veri belirteçleri işaretlemek ve filtrelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a8a8-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a8a8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0a8a8-104">Methods</span></span>  
  
|<span data-ttu-id="0a8a8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0a8a8-105">Method</span></span>|<span data-ttu-id="0a8a8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a8a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a8a8-107">IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a8a8-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="0a8a8-108">Belirtilen meta veri belirtecinin işlenip işlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="0a8a8-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="0a8a8-109">MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a8a8-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="0a8a8-110">Belirtilen meta veri belirtecinin işlendiğini gösteren değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0a8a8-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="0a8a8-111">UnmarkAll Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a8a8-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="0a8a8-112">Geçerli meta veri kapsamındaki tüm belirteçlerden işlem işaretlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0a8a8-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a8a8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a8a8-113">Requirements</span></span>  
 <span data-ttu-id="0a8a8-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a8a8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a8a8-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0a8a8-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a8a8-116">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0a8a8-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0a8a8-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a8a8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8a8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a8a8-118">See also</span></span>

- [<span data-ttu-id="0a8a8-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0a8a8-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
