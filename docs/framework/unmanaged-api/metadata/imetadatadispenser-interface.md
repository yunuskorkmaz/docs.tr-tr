---
title: IMetaDataDispenser Arabirimi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dda284fc86f0a82472c59d6bab08fd4a87364723
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225982"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="ad62b-102">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad62b-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="ad62b-103">Yeni bir meta veri kapsamı oluşturduğunuzda veya mevcut bir için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad62b-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad62b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ad62b-104">Methods</span></span>  
  
|<span data-ttu-id="ad62b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ad62b-105">Method</span></span>|<span data-ttu-id="ad62b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad62b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad62b-107">DefineScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad62b-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="ad62b-108">Yeni meta veri oluşturabileceğiniz bellekte yeni bir alan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ad62b-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="ad62b-109">OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad62b-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="ad62b-110">Var olan ve disk üzerindeki bir dosya açılır ve meta verileri belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="ad62b-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="ad62b-111">OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad62b-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="ad62b-112">Var olan meta veriler içeren belleği açılır.</span><span class="sxs-lookup"><span data-stu-id="ad62b-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="ad62b-113">Diğer bir deyişle, bu yöntem, var olan verilere meta veri olarak kabul edilir bellek belirtilen bir alan açılır.</span><span class="sxs-lookup"><span data-stu-id="ad62b-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad62b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad62b-114">Requirements</span></span>  
 <span data-ttu-id="ad62b-115">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad62b-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad62b-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ad62b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad62b-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ad62b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ad62b-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ad62b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad62b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad62b-119">See also</span></span>

- [<span data-ttu-id="ad62b-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad62b-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="ad62b-121">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad62b-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
