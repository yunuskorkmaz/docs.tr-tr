---
description: ': ICLRMetadataLocator arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6e7fd45197294563e12da020379d1bd54b088698
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772630"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="e3cf5-103">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3cf5-103">ICLRMetadataLocator Interface</span></span>

<span data-ttu-id="e3cf5-104">Hedef işlemdeki derlemelerin meta verilerini bulmak için veri erişim Hizmetleri katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3cf5-104">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3cf5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e3cf5-105">Methods</span></span>  
  
|<span data-ttu-id="e3cf5-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e3cf5-106">Method</span></span>|<span data-ttu-id="e3cf5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3cf5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3cf5-108">GetMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3cf5-108">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="e3cf5-109">Hedef işlemden bir görüntünün meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e3cf5-109">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3cf5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3cf5-110">Remarks</span></span>  

 <span data-ttu-id="e3cf5-111">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="e3cf5-111">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="e3cf5-112">Örneğin, canlı bir işlem için uygulama, bellek dökümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e3cf5-112">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3cf5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3cf5-113">Requirements</span></span>  

 <span data-ttu-id="e3cf5-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3cf5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3cf5-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e3cf5-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e3cf5-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e3cf5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3cf5-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3cf5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3cf5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3cf5-118">See also</span></span>

- [<span data-ttu-id="e3cf5-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e3cf5-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
