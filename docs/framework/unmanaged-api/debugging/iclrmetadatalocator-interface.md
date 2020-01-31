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
ms.openlocfilehash: 642391bce99328f3700d1783054943b6a450b22b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789025"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="e0f0e-102">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0f0e-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="e0f0e-103">Hedef işlemdeki derlemelerin meta verilerini bulmak için veri erişim Hizmetleri katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0f0e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e0f0e-104">Methods</span></span>  
  
|<span data-ttu-id="e0f0e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e0f0e-105">Method</span></span>|<span data-ttu-id="e0f0e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0f0e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0f0e-107">GetMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0f0e-107">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="e0f0e-108">Hedef işlemden bir görüntünün meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0f0e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0f0e-109">Remarks</span></span>  
 <span data-ttu-id="e0f0e-110">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="e0f0e-111">Örneğin, canlı bir işlem için uygulama, bellek dökümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0f0e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0f0e-112">Requirements</span></span>  
 <span data-ttu-id="e0f0e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0f0e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f0e-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e0f0e-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e0f0e-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e0f0e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0f0e-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f0e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f0e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0f0e-117">See also</span></span>

- [<span data-ttu-id="e0f0e-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0f0e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
