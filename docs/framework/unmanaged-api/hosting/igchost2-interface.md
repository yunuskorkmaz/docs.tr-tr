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
ms.openlocfilehash: 21ce9cbd007858c0f39e12622eff819154ab83f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928611"
---
# <a name="igchost2-interface"></a><span data-ttu-id="49210-102">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49210-102">IGCHost2 Interface</span></span>
<span data-ttu-id="49210-103">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="49210-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49210-104">Yeni geliştirme için, bunun yerine [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) arabirimini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="49210-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49210-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="49210-105">Methods</span></span>  
  
|<span data-ttu-id="49210-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="49210-106">Method</span></span>|<span data-ttu-id="49210-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49210-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49210-108">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49210-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="49210-109">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="49210-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="49210-110">1 `DWORD`. nesil ve kesim boyutlarını daha büyük olarak sunar.</span><span class="sxs-lookup"><span data-stu-id="49210-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49210-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49210-111">Requirements</span></span>  
 <span data-ttu-id="49210-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49210-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49210-113">**Üst bilgi** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="49210-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="49210-114">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="49210-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49210-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49210-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49210-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49210-116">See also</span></span>

- [<span data-ttu-id="49210-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="49210-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="49210-118">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="49210-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="49210-119">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="49210-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
