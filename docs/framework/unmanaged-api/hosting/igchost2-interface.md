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
ms.openlocfilehash: 742f738ca1a147c75b976d24fa4ac8e7fa4947c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622240"
---
# <a name="igchost2-interface"></a><span data-ttu-id="da864-102">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da864-102">IGCHost2 Interface</span></span>
<span data-ttu-id="da864-103">Çöp toplama işleminin bazı yönlerini denetleme ve çöp toplama sistemi hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="da864-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da864-104">Yeni geliştirme projeleri için biz kullanmanızı öneririz. [Iclrgcmanager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) bunun yerine arabirimi.</span><span class="sxs-lookup"><span data-stu-id="da864-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da864-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="da864-105">Methods</span></span>  
  
|<span data-ttu-id="da864-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="da864-106">Method</span></span>|<span data-ttu-id="da864-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da864-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da864-108">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da864-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="da864-109">Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="da864-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="da864-110">Nesil 0 ve büyük kesim boyutları sağlayan `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="da864-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da864-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da864-111">Requirements</span></span>  
 <span data-ttu-id="da864-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da864-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da864-113">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="da864-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="da864-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="da864-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da864-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da864-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da864-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da864-116">See also</span></span>
- [<span data-ttu-id="da864-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="da864-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="da864-118">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="da864-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="da864-119">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="da864-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
