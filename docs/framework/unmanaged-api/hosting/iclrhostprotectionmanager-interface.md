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
ms.openlocfilehash: c630fcd4667c8b19c4e21335549674d32508e439
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432842"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="3c6b2-102">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c6b2-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="3c6b2-103">Yönetilen sınıflar, yöntemler, özellikler ve kısmen güvenilen kodu çalıştırma alanların engellemek ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c6b2-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c6b2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3c6b2-104">Methods</span></span>  
  
|<span data-ttu-id="3c6b2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3c6b2-105">Method</span></span>|<span data-ttu-id="3c6b2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c6b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c6b2-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="3c6b2-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="3c6b2-108">Önemli ortak dil çalışma zamanı (CLR) hatalara neden olabilir. belirli nadir yarış durumları hiçbir zaman ortaya çıkar garanti sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c6b2-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="3c6b2-109">SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c6b2-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="3c6b2-110">Yönetilen türler ve kısmen güvenilen kodu çalıştırma engelleneceğini üyeleri kategorilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c6b2-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c6b2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c6b2-111">Requirements</span></span>  
 <span data-ttu-id="3c6b2-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c6b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c6b2-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c6b2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c6b2-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3c6b2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c6b2-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c6b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6b2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c6b2-116">See Also</span></span>  
 [<span data-ttu-id="3c6b2-117">EApiCategories Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3c6b2-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="3c6b2-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c6b2-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
