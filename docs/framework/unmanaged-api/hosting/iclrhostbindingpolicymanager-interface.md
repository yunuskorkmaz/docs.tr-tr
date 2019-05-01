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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e494bbbd08a77329b7b64816216e4bb2e1b724a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984678"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="eaf58-102">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaf58-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="eaf58-103">Geçerli bağlama ilkesi değerlendirmek ve ilke değişikliklerini iletişim kurmak için belirtilen bir derleme ana bilgisayar için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaf58-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eaf58-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eaf58-104">Methods</span></span>  
  
|<span data-ttu-id="eaf58-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eaf58-105">Method</span></span>|<span data-ttu-id="eaf58-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eaf58-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eaf58-107">EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaf58-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="eaf58-108">Bağlama ilkesi, konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="eaf58-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="eaf58-109">ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaf58-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="eaf58-110">Belirtilen derleme için bağlama ilkesi değiştirir ve ilke yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eaf58-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eaf58-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eaf58-111">Requirements</span></span>  
 <span data-ttu-id="eaf58-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaf58-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf58-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eaf58-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eaf58-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="eaf58-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaf58-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf58-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf58-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaf58-116">See also</span></span>

- [<span data-ttu-id="eaf58-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaf58-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="eaf58-118">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaf58-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="eaf58-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eaf58-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
