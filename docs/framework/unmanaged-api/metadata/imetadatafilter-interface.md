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
ms.openlocfilehash: ad77aba02c819749794534ca2ecd478661bc363f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444987"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="18e45-102">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18e45-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="18e45-103">İşaretleme ve zaten gerçekleştirilecek eylemler yinelenen önlemek için meta veri simgesi filtreleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="18e45-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18e45-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="18e45-104">Methods</span></span>  
  
|<span data-ttu-id="18e45-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="18e45-105">Method</span></span>|<span data-ttu-id="18e45-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18e45-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18e45-107">IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18e45-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="18e45-108">Belirtilen meta veri simgesi işlenen olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="18e45-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="18e45-109">MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18e45-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="18e45-110">Belirtilen meta veri simgesi işlenmiş belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="18e45-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="18e45-111">UnmarkAll Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18e45-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="18e45-112">Geçerli meta veri kapsamdaki tüm belirteçleri işleme işaretleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="18e45-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18e45-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18e45-113">Requirements</span></span>  
 <span data-ttu-id="18e45-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18e45-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18e45-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18e45-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18e45-116">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="18e45-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18e45-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18e45-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e45-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18e45-118">See Also</span></span>  
 [<span data-ttu-id="18e45-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="18e45-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
