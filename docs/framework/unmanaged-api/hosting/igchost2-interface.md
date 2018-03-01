---
title: IGCHost2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a616e724d6fb26734fcda48d6a9b39605e0284a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="igchost2-interface"></a><span data-ttu-id="04d19-102">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04d19-102">IGCHost2 Interface</span></span>
<span data-ttu-id="04d19-103">Çöp toplama sistemi hakkında bilgi edinme ve atık toplama bazı yönlerini denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="04d19-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04d19-104">Yeni geliştirme projeleri için kullanmanızı öneririz [Iclrgcmanager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) yerine arabirim.</span><span class="sxs-lookup"><span data-stu-id="04d19-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04d19-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="04d19-105">Methods</span></span>  
  
|<span data-ttu-id="04d19-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="04d19-106">Method</span></span>|<span data-ttu-id="04d19-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04d19-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04d19-108">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04d19-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="04d19-109">Kesim boyutu ve en büyük boyutu 0 oluşturma için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="04d19-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="04d19-110">Kuşak 0 ve büyük kesim boyutları sağlayan `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="04d19-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04d19-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04d19-111">Requirements</span></span>  
 <span data-ttu-id="04d19-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04d19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04d19-113">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="04d19-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="04d19-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="04d19-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04d19-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04d19-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d19-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04d19-116">See Also</span></span>  
 [<span data-ttu-id="04d19-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04d19-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="04d19-118">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04d19-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="04d19-119">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="04d19-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
