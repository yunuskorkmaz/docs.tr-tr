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
ms.openlocfilehash: 1d4cb310215967a79e43e43319e107b6c42551e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557441"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="f43f6-102">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f43f6-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="f43f6-103">Yönetilen sınıflar, yöntemler, özellikler ve alanları kısmen güvenilen kod çalıştırılmasını engellemek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f43f6-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f43f6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f43f6-104">Methods</span></span>  
  
|<span data-ttu-id="f43f6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f43f6-105">Method</span></span>|<span data-ttu-id="f43f6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f43f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f43f6-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="f43f6-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="f43f6-108">Önemli ortak dil çalışma zamanı (CLR) hatalara neden olabilir. bazı nadir yarış durumlarını hiçbir zaman ortaya garantisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f43f6-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="f43f6-109">SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f43f6-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="f43f6-110">Yönetilen türler ve kısmen güvenilen kod çalıştırılmasının engellenmesi gerektiğini üyeleri kategorilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f43f6-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f43f6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f43f6-111">Requirements</span></span>  
 <span data-ttu-id="f43f6-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f43f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f43f6-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f43f6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f43f6-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f43f6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f43f6-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f43f6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43f6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f43f6-116">See also</span></span>
- [<span data-ttu-id="f43f6-117">EApiCategories Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f43f6-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="f43f6-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f43f6-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
