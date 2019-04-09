---
title: IGCHost2 Arabirimi
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75bef91eb70c8109653741452362cd2e85f625ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138144"
---
# <a name="igchost2-interface"></a><span data-ttu-id="74ee2-102">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74ee2-102">IGCHost2 Interface</span></span>
<span data-ttu-id="74ee2-103">Çöp toplama işleminin bazı yönlerini denetleme ve çöp toplama sistemi hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="74ee2-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74ee2-104">Yeni geliştirme projeleri için biz kullanmanızı öneririz. [Iclrgcmanager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) bunun yerine arabirimi.</span><span class="sxs-lookup"><span data-stu-id="74ee2-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74ee2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="74ee2-105">Methods</span></span>  
  
|<span data-ttu-id="74ee2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="74ee2-106">Method</span></span>|<span data-ttu-id="74ee2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74ee2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74ee2-108">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74ee2-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="74ee2-109">Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="74ee2-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="74ee2-110">Nesil 0 ve büyük kesim boyutları sağlayan `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="74ee2-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74ee2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74ee2-111">Requirements</span></span>  
 <span data-ttu-id="74ee2-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ee2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ee2-113">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="74ee2-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="74ee2-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="74ee2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="74ee2-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="74ee2-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="74ee2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74ee2-116">See also</span></span>

- [<span data-ttu-id="74ee2-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74ee2-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="74ee2-118">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74ee2-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="74ee2-119">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="74ee2-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
