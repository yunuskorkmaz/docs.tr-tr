---
title: ICLRHostBindingPolicyManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
ms.openlocfilehash: 9ed317a451e6e35aeac3bc1b83f78d1400ea5c07
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136435"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="ef162-102">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef162-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="ef162-103">Ana bilgisayarın geçerli bağlama ilkesini değerlendirmesi ve belirtilen bir derlemede ilke değişikliklerini iletişim kurması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef162-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef162-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ef162-104">Methods</span></span>  
  
|<span data-ttu-id="ef162-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ef162-105">Method</span></span>|<span data-ttu-id="ef162-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef162-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef162-107">EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef162-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="ef162-108">Bağlama ilkesini konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="ef162-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="ef162-109">ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef162-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="ef162-110">Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef162-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef162-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef162-111">Requirements</span></span>  
 <span data-ttu-id="ef162-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef162-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef162-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ef162-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef162-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ef162-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef162-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef162-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef162-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef162-116">See also</span></span>

- [<span data-ttu-id="ef162-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef162-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ef162-118">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef162-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="ef162-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ef162-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
