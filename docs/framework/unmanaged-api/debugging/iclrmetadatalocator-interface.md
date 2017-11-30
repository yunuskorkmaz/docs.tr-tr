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
ms.openlocfilehash: 955bd6bffe56a166b4c9c313fcb730ce714bf24b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="0f5bb-102">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f5bb-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="0f5bb-103">Bir hedef işlemde derlemelerin meta verileri bulmak için veri erişim Hizmetleri katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f5bb-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f5bb-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0f5bb-104">Methods</span></span>  
  
|<span data-ttu-id="0f5bb-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0f5bb-105">Method</span></span>|<span data-ttu-id="0f5bb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f5bb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f5bb-107">GetMetadata yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f5bb-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="0f5bb-108">Görüntü meta verilerini hedef işleminden alır.</span><span class="sxs-lookup"><span data-stu-id="0f5bb-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f5bb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f5bb-109">Remarks</span></span>  
 <span data-ttu-id="0f5bb-110">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="0f5bb-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="0f5bb-111">Örneğin, canlı bir işlem uygulamasını bir bellek dökümü farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0f5bb-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f5bb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f5bb-112">Requirements</span></span>  
 <span data-ttu-id="0f5bb-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f5bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f5bb-114">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0f5bb-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0f5bb-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f5bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f5bb-116">**.**</span><span class="sxs-lookup"><span data-stu-id="0f5bb-116">**.**</span></span> <span data-ttu-id="0f5bb-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f5bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f5bb-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f5bb-118">See Also</span></span>  
 [<span data-ttu-id="0f5bb-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f5bb-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
