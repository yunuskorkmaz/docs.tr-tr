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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944679"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="d5a51-102">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5a51-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="d5a51-103">Yönetilen sınıflar, yöntemler, özellikler ve alanları kısmen güvenilen kod çalıştırılmasını engellemek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5a51-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5a51-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d5a51-104">Methods</span></span>  
  
|<span data-ttu-id="d5a51-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d5a51-105">Method</span></span>|<span data-ttu-id="d5a51-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5a51-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5a51-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="d5a51-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="d5a51-108">Önemli ortak dil çalışma zamanı (CLR) hatalara neden olabilir. bazı nadir yarış durumlarını hiçbir zaman ortaya garantisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5a51-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="d5a51-109">SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5a51-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="d5a51-110">Yönetilen türler ve kısmen güvenilen kod çalıştırılmasının engellenmesi gerektiğini üyeleri kategorilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5a51-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5a51-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5a51-111">Requirements</span></span>  
 <span data-ttu-id="d5a51-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a51-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a51-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5a51-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5a51-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d5a51-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5a51-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5a51-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a51-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5a51-116">See also</span></span>

- [<span data-ttu-id="d5a51-117">EApiCategories Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d5a51-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="d5a51-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5a51-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
