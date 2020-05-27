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
ms.openlocfilehash: 2bdfe65dbf923ec61d91a259b5257d892fef53da
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007344"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="e5ccf-102">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5ccf-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="e5ccf-103">Yeni bir meta veri kapsamı oluşturmak için yöntemler sağlar veya var olan bir verileri açar.</span><span class="sxs-lookup"><span data-stu-id="e5ccf-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5ccf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5ccf-104">Methods</span></span>  
  
|<span data-ttu-id="e5ccf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e5ccf-105">Method</span></span>|<span data-ttu-id="e5ccf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5ccf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5ccf-107">DefineScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5ccf-107">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="e5ccf-108">Bellekte yeni meta veri oluşturabileceğiniz yeni bir alan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5ccf-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="e5ccf-109">OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5ccf-109">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="e5ccf-110">Mevcut, disk üzerindeki bir dosyayı açar ve meta verilerini belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="e5ccf-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="e5ccf-111">OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5ccf-111">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="e5ccf-112">Mevcut meta verileri içeren bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="e5ccf-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="e5ccf-113">Diğer bir deyişle, bu yöntem mevcut verilerin meta veri olarak değerlendirilme belirtilen bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="e5ccf-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5ccf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5ccf-114">Requirements</span></span>  
 <span data-ttu-id="e5ccf-115">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ccf-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ccf-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e5ccf-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5ccf-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e5ccf-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5ccf-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ccf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ccf-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5ccf-119">See also</span></span>

- [<span data-ttu-id="e5ccf-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5ccf-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="e5ccf-121">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e5ccf-121">Metadata Interfaces</span></span>](metadata-interfaces.md)
