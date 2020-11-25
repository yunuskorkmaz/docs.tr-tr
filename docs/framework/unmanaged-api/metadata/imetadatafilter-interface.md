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
ms.openlocfilehash: 2c22e45ca3d33b0a81ff0ecd90bf7574c45676bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701854"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="09ae4-102">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09ae4-102">IMetaDataFilter Interface</span></span>

<span data-ttu-id="09ae4-103">Zaten alınmış olan işlemleri önlemek için meta veri belirteçleri işaretlemek ve filtrelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="09ae4-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09ae4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="09ae4-104">Methods</span></span>  
  
|<span data-ttu-id="09ae4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="09ae4-105">Method</span></span>|<span data-ttu-id="09ae4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09ae4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09ae4-107">IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09ae4-107">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="09ae4-108">Belirtilen meta veri belirtecinin işlenip işlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="09ae4-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="09ae4-109">MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09ae4-109">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="09ae4-110">Belirtilen meta veri belirtecinin işlendiğini gösteren değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="09ae4-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="09ae4-111">UnmarkAll Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09ae4-111">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="09ae4-112">Geçerli meta veri kapsamındaki tüm belirteçlerden işlem işaretlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="09ae4-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09ae4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09ae4-113">Requirements</span></span>  

 <span data-ttu-id="09ae4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09ae4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ae4-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="09ae4-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09ae4-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="09ae4-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09ae4-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ae4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ae4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09ae4-118">See also</span></span>

- [<span data-ttu-id="09ae4-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="09ae4-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
