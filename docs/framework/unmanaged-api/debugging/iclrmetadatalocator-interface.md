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
ms.openlocfilehash: fd7a67237d89864915f8b4f1f7361d1f113d1e5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404751"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="54490-102">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54490-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="54490-103">Bir hedef işlemde derlemelerin meta verileri bulmak için veri erişim Hizmetleri katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54490-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54490-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="54490-104">Methods</span></span>  
  
|<span data-ttu-id="54490-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="54490-105">Method</span></span>|<span data-ttu-id="54490-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54490-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54490-107">GetMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54490-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="54490-108">Görüntü meta verilerini hedef işleminden alır.</span><span class="sxs-lookup"><span data-stu-id="54490-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54490-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54490-109">Remarks</span></span>  
 <span data-ttu-id="54490-110">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="54490-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="54490-111">Örneğin, canlı bir işlem uygulamasını bir bellek dökümü farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="54490-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54490-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54490-112">Requirements</span></span>  
 <span data-ttu-id="54490-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54490-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54490-114">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="54490-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="54490-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54490-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54490-116">**.**</span><span class="sxs-lookup"><span data-stu-id="54490-116">**.**</span></span> <span data-ttu-id="54490-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54490-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54490-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54490-118">See Also</span></span>  
 [<span data-ttu-id="54490-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="54490-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
