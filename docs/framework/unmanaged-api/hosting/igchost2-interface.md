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
ms.openlocfilehash: 43c16415c91521194e0d88be84dd176c3fdadad1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134844"
---
# <a name="igchost2-interface"></a><span data-ttu-id="fcda6-102">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcda6-102">IGCHost2 Interface</span></span>
<span data-ttu-id="fcda6-103">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcda6-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcda6-104">Yeni geliştirme için, bunun yerine [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) arabirimini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="fcda6-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcda6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fcda6-105">Methods</span></span>  
  
|<span data-ttu-id="fcda6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fcda6-106">Method</span></span>|<span data-ttu-id="fcda6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcda6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fcda6-108">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcda6-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="fcda6-109">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fcda6-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="fcda6-110">Nesil 0 ve kesim boyutlarını `DWORD`daha büyük bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="fcda6-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fcda6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcda6-111">Requirements</span></span>  
 <span data-ttu-id="fcda6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcda6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcda6-113">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="fcda6-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="fcda6-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fcda6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcda6-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcda6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcda6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcda6-116">See also</span></span>

- [<span data-ttu-id="fcda6-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fcda6-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="fcda6-118">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fcda6-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="fcda6-119">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="fcda6-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
