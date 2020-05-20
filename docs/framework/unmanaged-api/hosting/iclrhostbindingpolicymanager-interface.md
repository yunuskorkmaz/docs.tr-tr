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
ms.openlocfilehash: 3cf2a945607bf85a51dbec35342ff5ac46878bca
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703572"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="ed162-102">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed162-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="ed162-103">Ana bilgisayarın geçerli bağlama ilkesini değerlendirmesi ve belirtilen bir derlemede ilke değişikliklerini iletişim kurması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed162-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed162-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ed162-104">Methods</span></span>  
  
|<span data-ttu-id="ed162-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ed162-105">Method</span></span>|<span data-ttu-id="ed162-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed162-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ed162-107">EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed162-107">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="ed162-108">Bağlama ilkesini konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="ed162-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="ed162-109">ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed162-109">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="ed162-110">Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed162-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed162-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed162-111">Requirements</span></span>  
 <span data-ttu-id="ed162-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed162-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed162-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ed162-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed162-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ed162-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed162-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed162-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed162-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed162-116">See also</span></span>

- [<span data-ttu-id="ed162-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed162-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ed162-118">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed162-118">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="ed162-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ed162-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
