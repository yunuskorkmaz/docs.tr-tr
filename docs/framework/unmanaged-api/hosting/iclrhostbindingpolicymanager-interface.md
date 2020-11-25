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
ms.openlocfilehash: 49d1ee4dd0965d4ae5b54b53208809cfbdf7e718
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725641"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="6e510-102">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e510-102">ICLRHostBindingPolicyManager Interface</span></span>

<span data-ttu-id="6e510-103">Ana bilgisayarın geçerli bağlama ilkesini değerlendirmesi ve belirtilen bir derlemede ilke değişikliklerini iletişim kurması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e510-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e510-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e510-104">Methods</span></span>  
  
|<span data-ttu-id="6e510-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6e510-105">Method</span></span>|<span data-ttu-id="6e510-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e510-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e510-107">EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e510-107">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="6e510-108">Bağlama ilkesini konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6e510-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="6e510-109">ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e510-109">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="6e510-110">Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e510-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e510-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e510-111">Requirements</span></span>  

 <span data-ttu-id="6e510-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e510-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e510-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6e510-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e510-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6e510-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e510-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e510-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e510-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e510-116">See also</span></span>

- [<span data-ttu-id="6e510-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e510-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6e510-118">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e510-118">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="6e510-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e510-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
