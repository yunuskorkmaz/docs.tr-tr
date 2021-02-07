---
description: ': IMetaDataFilter arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c994574207ccb26a5cb317e1673145a41f0d837d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677932"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="43ec3-103">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43ec3-103">IMetaDataFilter Interface</span></span>

<span data-ttu-id="43ec3-104">Zaten alınmış olan işlemleri önlemek için meta veri belirteçleri işaretlemek ve filtrelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="43ec3-104">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43ec3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="43ec3-105">Methods</span></span>  
  
|<span data-ttu-id="43ec3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="43ec3-106">Method</span></span>|<span data-ttu-id="43ec3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43ec3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43ec3-108">IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43ec3-108">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="43ec3-109">Belirtilen meta veri belirtecinin işlenip işlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="43ec3-109">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="43ec3-110">MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43ec3-110">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="43ec3-111">Belirtilen meta veri belirtecinin işlendiğini gösteren değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="43ec3-111">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="43ec3-112">UnmarkAll Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43ec3-112">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="43ec3-113">Geçerli meta veri kapsamındaki tüm belirteçlerden işlem işaretlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="43ec3-113">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43ec3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43ec3-114">Requirements</span></span>  

 <span data-ttu-id="43ec3-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43ec3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ec3-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="43ec3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43ec3-117">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="43ec3-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43ec3-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ec3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ec3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43ec3-119">See also</span></span>

- [<span data-ttu-id="43ec3-120">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="43ec3-120">Metadata Interfaces</span></span>](metadata-interfaces.md)
