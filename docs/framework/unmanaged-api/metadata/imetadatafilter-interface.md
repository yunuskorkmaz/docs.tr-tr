---
title: IMetaDataFilter Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter
helpviewer_keywords: IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0918802a146940fb7579279e56f752bd114c746c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="08ac8-102">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08ac8-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="08ac8-103">İşaretleme ve zaten gerçekleştirilecek eylemler yinelenen önlemek için meta veri simgesi filtreleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="08ac8-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08ac8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="08ac8-104">Methods</span></span>  
  
|<span data-ttu-id="08ac8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="08ac8-105">Method</span></span>|<span data-ttu-id="08ac8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08ac8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08ac8-107">IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08ac8-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="08ac8-108">Belirtilen meta veri simgesi işlenen olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="08ac8-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="08ac8-109">MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08ac8-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="08ac8-110">Belirtilen meta veri simgesi işlenmiş belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="08ac8-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="08ac8-111">UnmarkAll Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08ac8-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="08ac8-112">Geçerli meta veri kapsamdaki tüm belirteçleri işleme işaretleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="08ac8-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08ac8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08ac8-113">Requirements</span></span>  
 <span data-ttu-id="08ac8-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08ac8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08ac8-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08ac8-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08ac8-116">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="08ac8-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08ac8-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08ac8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ac8-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08ac8-118">See Also</span></span>  
 [<span data-ttu-id="08ac8-119">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08ac8-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
