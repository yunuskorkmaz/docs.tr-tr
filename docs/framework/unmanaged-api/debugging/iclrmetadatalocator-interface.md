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
ms.openlocfilehash: ec92214e33cd1acda8b2702d93deba1f0fb2aaa2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111025"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="dbeaf-102">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbeaf-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="dbeaf-103">Hedef işlemdeki derlemelerin meta verilerini bulmak için veri erişim Hizmetleri katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dbeaf-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbeaf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dbeaf-104">Methods</span></span>  
  
|<span data-ttu-id="dbeaf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dbeaf-105">Method</span></span>|<span data-ttu-id="dbeaf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbeaf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbeaf-107">GetMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dbeaf-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="dbeaf-108">Hedef işlemden bir görüntünün meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="dbeaf-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbeaf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbeaf-109">Remarks</span></span>  
 <span data-ttu-id="dbeaf-110">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="dbeaf-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="dbeaf-111">Örneğin, canlı bir işlem için uygulama, bellek dökümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dbeaf-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbeaf-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbeaf-112">Requirements</span></span>  
 <span data-ttu-id="dbeaf-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbeaf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbeaf-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="dbeaf-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dbeaf-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dbeaf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbeaf-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbeaf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbeaf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbeaf-117">See also</span></span>

- [<span data-ttu-id="dbeaf-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dbeaf-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
