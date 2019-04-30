---
title: ICLRMetadataLocator Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddc0429a6fa921e8e6ba3c55f3efe5373bea9576
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697855"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="4f050-102">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f050-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="4f050-103">Hedef işlemde derlemelerin meta verileri bulmak için veri erişim Hizmetleri düzeyi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f050-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f050-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4f050-104">Methods</span></span>  
  
|<span data-ttu-id="4f050-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4f050-105">Method</span></span>|<span data-ttu-id="4f050-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f050-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f050-107">GetMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f050-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="4f050-108">Hedef işlemden görüntü meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="4f050-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f050-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f050-109">Remarks</span></span>  
 <span data-ttu-id="4f050-110">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="4f050-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="4f050-111">Örneğin, uygulama canlı bir işlem için bellek dökümü farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4f050-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f050-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f050-112">Requirements</span></span>  
 <span data-ttu-id="4f050-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f050-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f050-114">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4f050-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4f050-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f050-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f050-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f050-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f050-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f050-117">See also</span></span>

- [<span data-ttu-id="4f050-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4f050-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
