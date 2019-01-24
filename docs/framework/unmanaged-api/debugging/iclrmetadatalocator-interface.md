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
ms.openlocfilehash: 5d1d767de88b239c96cb98130b6ff006e3f75b09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495038"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="88959-102">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88959-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="88959-103">Hedef işlemde derlemelerin meta verileri bulmak için veri erişim Hizmetleri düzeyi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88959-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88959-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="88959-104">Methods</span></span>  
  
|<span data-ttu-id="88959-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="88959-105">Method</span></span>|<span data-ttu-id="88959-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88959-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88959-107">GetMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88959-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="88959-108">Hedef işlemden görüntü meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="88959-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88959-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88959-109">Remarks</span></span>  
 <span data-ttu-id="88959-110">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="88959-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="88959-111">Örneğin, uygulama canlı bir işlem için bellek dökümü farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="88959-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88959-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88959-112">Requirements</span></span>  
 <span data-ttu-id="88959-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88959-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88959-114">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="88959-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="88959-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88959-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88959-116">**.**</span><span class="sxs-lookup"><span data-stu-id="88959-116">**.**</span></span> <span data-ttu-id="88959-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88959-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88959-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88959-118">See also</span></span>
- [<span data-ttu-id="88959-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="88959-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
