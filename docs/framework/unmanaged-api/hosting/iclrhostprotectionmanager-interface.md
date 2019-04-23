---
title: ICLRHostProtectionManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd096344c987d8901f0baab86e370abbb03528e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177781"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="a46a8-102">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a46a8-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="a46a8-103">Yönetilen sınıflar, yöntemler, özellikler ve alanları kısmen güvenilen kod çalıştırılmasını engellemek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a46a8-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a46a8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a46a8-104">Methods</span></span>  
  
|<span data-ttu-id="a46a8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a46a8-105">Method</span></span>|<span data-ttu-id="a46a8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a46a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a46a8-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="a46a8-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="a46a8-108">Önemli ortak dil çalışma zamanı (CLR) hatalara neden olabilir. bazı nadir yarış durumlarını hiçbir zaman ortaya garantisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a46a8-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="a46a8-109">SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a46a8-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="a46a8-110">Yönetilen türler ve kısmen güvenilen kod çalıştırılmasının engellenmesi gerektiğini üyeleri kategorilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a46a8-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a46a8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a46a8-111">Requirements</span></span>  
 <span data-ttu-id="a46a8-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a46a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a46a8-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a46a8-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a46a8-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a46a8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a46a8-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a46a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a46a8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a46a8-116">See also</span></span>

- [<span data-ttu-id="a46a8-117">EApiCategories Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a46a8-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="a46a8-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a46a8-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
