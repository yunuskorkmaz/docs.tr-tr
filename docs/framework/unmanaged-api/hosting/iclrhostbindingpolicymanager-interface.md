---
description: ': ICLRHostBindingPolicyManager arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 07a18d622ff8d8483fe6dcb0242cb5f1ee284b14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789950"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="8cec2-103">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cec2-103">ICLRHostBindingPolicyManager Interface</span></span>

<span data-ttu-id="8cec2-104">Ana bilgisayarın geçerli bağlama ilkesini değerlendirmesi ve belirtilen bir derlemede ilke değişikliklerini iletişim kurması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cec2-104">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cec2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8cec2-105">Methods</span></span>  
  
|<span data-ttu-id="8cec2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8cec2-106">Method</span></span>|<span data-ttu-id="8cec2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cec2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cec2-108">EvaluatePolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cec2-108">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="8cec2-109">Bağlama ilkesini konak adına değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8cec2-109">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="8cec2-110">ModifyApplicationPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cec2-110">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="8cec2-111">Belirtilen derleme için bağlama ilkesini değiştirir ve ilkenin yeni bir sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8cec2-111">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cec2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cec2-112">Requirements</span></span>  

 <span data-ttu-id="8cec2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cec2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cec2-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8cec2-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cec2-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8cec2-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cec2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cec2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cec2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cec2-117">See also</span></span>

- [<span data-ttu-id="8cec2-118">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cec2-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8cec2-119">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cec2-119">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="8cec2-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8cec2-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
