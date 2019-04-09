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
ms.openlocfilehash: 4196ff2cb2d4ebc401076f603a8a7fdc9b9c76ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143799"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="d919c-102">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d919c-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="d919c-103">İşaretleme ve meta veri belirteçleri zaten alınmış eylemleri tekrarlamayı önlemek üzere filtreleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d919c-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d919c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d919c-104">Methods</span></span>  
  
|<span data-ttu-id="d919c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d919c-105">Method</span></span>|<span data-ttu-id="d919c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d919c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d919c-107">IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d919c-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="d919c-108">Belirtilen meta veri belirteci işlenen olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d919c-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="d919c-109">MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d919c-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="d919c-110">Belirtilen meta veri belirteci işlendiğini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d919c-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="d919c-111">UnmarkAll Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d919c-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="d919c-112">Geçerli meta veri kapsamdaki tüm belirteçlerin işleme işaretleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d919c-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d919c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d919c-113">Requirements</span></span>  
 <span data-ttu-id="d919c-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d919c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d919c-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d919c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d919c-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="d919c-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d919c-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d919c-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d919c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d919c-118">See also</span></span>

- [<span data-ttu-id="d919c-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d919c-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
