---
title: IMetaDataDispenser Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 678796357b36beb26ebbf34edc713ff6f15a7c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="364d3-102">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="364d3-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="364d3-103">Yeni bir meta veri kapsamı oluşturmak veya mevcut bir açmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="364d3-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="364d3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="364d3-104">Methods</span></span>  
  
|<span data-ttu-id="364d3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="364d3-105">Method</span></span>|<span data-ttu-id="364d3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="364d3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="364d3-107">DefineScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="364d3-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="364d3-108">Yeni bir alan yeni meta oluşturabileceğiniz bellekte oluşturur.</span><span class="sxs-lookup"><span data-stu-id="364d3-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="364d3-109">OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="364d3-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="364d3-110">Var olan, disk üzerindeki bir dosyayı açar ve belleğe meta verilerini eşler.</span><span class="sxs-lookup"><span data-stu-id="364d3-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="364d3-111">OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="364d3-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="364d3-112">Var olan meta veriler içeren bellek alanı açılır.</span><span class="sxs-lookup"><span data-stu-id="364d3-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="364d3-113">Diğer bir deyişle, bu yöntem belirtilen alan var olan verileri meta verileri kabul edilir bellek açar.</span><span class="sxs-lookup"><span data-stu-id="364d3-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="364d3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="364d3-114">Requirements</span></span>  
 <span data-ttu-id="364d3-115">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="364d3-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="364d3-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="364d3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="364d3-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="364d3-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="364d3-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="364d3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="364d3-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="364d3-119">See Also</span></span>  
 [<span data-ttu-id="364d3-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="364d3-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="364d3-121">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="364d3-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
