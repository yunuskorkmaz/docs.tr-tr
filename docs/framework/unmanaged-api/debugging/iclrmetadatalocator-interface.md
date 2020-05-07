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
ms.openlocfilehash: 734f8eaa7c520bbf1ad1208ece42751e967a208a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859723"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="af8bf-102">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af8bf-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="af8bf-103">Hedef işlemdeki derlemelerin meta verilerini bulmak için veri erişim Hizmetleri katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af8bf-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af8bf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="af8bf-104">Methods</span></span>  
  
|<span data-ttu-id="af8bf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="af8bf-105">Method</span></span>|<span data-ttu-id="af8bf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af8bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af8bf-107">GetMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af8bf-107">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="af8bf-108">Hedef işlemden bir görüntünün meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="af8bf-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af8bf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af8bf-109">Remarks</span></span>  
 <span data-ttu-id="af8bf-110">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="af8bf-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="af8bf-111">Örneğin, canlı bir işlem için uygulama, bellek dökümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="af8bf-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af8bf-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af8bf-112">Requirements</span></span>  
 <span data-ttu-id="af8bf-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af8bf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af8bf-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="af8bf-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="af8bf-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="af8bf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af8bf-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8bf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af8bf-117">See also</span></span>

- [<span data-ttu-id="af8bf-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="af8bf-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
