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
ms.openlocfilehash: 7c0afbb9be9af3ffe69ddfcac85b70de53a391ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="dc96a-102">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc96a-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="dc96a-103">İşaretleme ve zaten gerçekleştirilecek eylemler yinelenen önlemek için meta veri simgesi filtreleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc96a-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc96a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dc96a-104">Methods</span></span>  
  
|<span data-ttu-id="dc96a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dc96a-105">Method</span></span>|<span data-ttu-id="dc96a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc96a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc96a-107">Istokenmarked yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc96a-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="dc96a-108">Belirtilen meta veri simgesi işlenen olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="dc96a-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="dc96a-109">MarkToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc96a-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="dc96a-110">Belirtilen meta veri simgesi işlenmiş belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dc96a-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="dc96a-111">UnmarkAll yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc96a-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="dc96a-112">Geçerli meta veri kapsamdaki tüm belirteçleri işleme işaretleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dc96a-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc96a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc96a-113">Requirements</span></span>  
 <span data-ttu-id="dc96a-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc96a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc96a-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc96a-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc96a-116">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dc96a-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc96a-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc96a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc96a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc96a-118">See Also</span></span>  
 [<span data-ttu-id="dc96a-119">Meta veri arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc96a-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
