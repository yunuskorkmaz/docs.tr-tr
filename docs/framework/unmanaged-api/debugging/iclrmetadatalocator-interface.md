---
title: ICLRMetadataLocator Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator
helpviewer_keywords: ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a06997c47a85ced56dc579759192f7256def4f5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="223a8-102">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="223a8-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="223a8-103">Bir hedef işlemde derlemelerin meta verileri bulmak için veri erişim Hizmetleri katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="223a8-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="223a8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="223a8-104">Methods</span></span>  
  
|<span data-ttu-id="223a8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="223a8-105">Method</span></span>|<span data-ttu-id="223a8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="223a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="223a8-107">GetMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="223a8-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="223a8-108">Görüntü meta verilerini hedef işleminden alır.</span><span class="sxs-lookup"><span data-stu-id="223a8-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="223a8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="223a8-109">Remarks</span></span>  
 <span data-ttu-id="223a8-110">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="223a8-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="223a8-111">Örneğin, canlı bir işlem uygulamasını bir bellek dökümü farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="223a8-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="223a8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="223a8-112">Requirements</span></span>  
 <span data-ttu-id="223a8-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="223a8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="223a8-114">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="223a8-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="223a8-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="223a8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="223a8-116">**.**</span><span class="sxs-lookup"><span data-stu-id="223a8-116">**.**</span></span> <span data-ttu-id="223a8-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="223a8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="223a8-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="223a8-118">See Also</span></span>  
 [<span data-ttu-id="223a8-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="223a8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
