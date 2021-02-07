---
description: ': Imetadatadağıtıcı arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5ba37fc05a4e1897b100967d32b268f91a0e4402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721014"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="e15cb-103">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e15cb-103">IMetaDataDispenser Interface</span></span>

<span data-ttu-id="e15cb-104">Yeni bir meta veri kapsamı oluşturmak için yöntemler sağlar veya var olan bir verileri açar.</span><span class="sxs-lookup"><span data-stu-id="e15cb-104">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e15cb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e15cb-105">Methods</span></span>  
  
|<span data-ttu-id="e15cb-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e15cb-106">Method</span></span>|<span data-ttu-id="e15cb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e15cb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e15cb-108">DefineScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e15cb-108">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="e15cb-109">Bellekte yeni meta veri oluşturabileceğiniz yeni bir alan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e15cb-109">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="e15cb-110">OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e15cb-110">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="e15cb-111">Mevcut, disk üzerindeki bir dosyayı açar ve meta verilerini belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="e15cb-111">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="e15cb-112">OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e15cb-112">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="e15cb-113">Mevcut meta verileri içeren bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="e15cb-113">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="e15cb-114">Diğer bir deyişle, bu yöntem mevcut verilerin meta veri olarak değerlendirilme belirtilen bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="e15cb-114">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e15cb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e15cb-115">Requirements</span></span>  

 <span data-ttu-id="e15cb-116">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e15cb-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e15cb-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e15cb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e15cb-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e15cb-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e15cb-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e15cb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e15cb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e15cb-120">See also</span></span>

- [<span data-ttu-id="e15cb-121">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e15cb-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="e15cb-122">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e15cb-122">Metadata Interfaces</span></span>](metadata-interfaces.md)
