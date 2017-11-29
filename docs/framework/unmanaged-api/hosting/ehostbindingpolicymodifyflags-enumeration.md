---
title: "EHostBindingPolicyModifyFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EHostBindingPolicyModifyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EHostBindingPolicyModifyFlags
helpviewer_keywords: EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ff7ec7487be649e353b48e537cf1d8d45f6962
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="cf789-102">EHostBindingPolicyModifyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cf789-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="cf789-103">Ortak dil çalışma zamanı (CLR) bir hedef derleme kaynak derlemesinden İlkesi değişiklikleri uygularken gerçekleştirmesi gereken yeniden yönlendirme türü belirtmek ana bilgisayar tanır.</span><span class="sxs-lookup"><span data-stu-id="cf789-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf789-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf789-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cf789-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cf789-105">Members</span></span>  
  
|<span data-ttu-id="cf789-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cf789-106">Member</span></span>|<span data-ttu-id="cf789-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf789-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="cf789-108">CLR ilke değerleri bu hedef derlemenin üzerine kaynak derlemenin zincirine bağlı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf789-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="cf789-109">CLR varsayılan eylem gerçekleştireceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf789-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="cf789-110">CLR en yüksek değerleri hedef derlemenin ilke değerleri ayarlamak belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf789-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="cf789-111">CLR İlkesi değerleri hedef derlemenin kaynak assembly olanlar değiştirir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf789-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf789-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf789-112">Remarks</span></span>  
 <span data-ttu-id="cf789-113">[Iclrhostbindingpolicymanager::modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) yöntemi türünde bir parametre alan `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="cf789-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf789-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf789-114">Requirements</span></span>  
 <span data-ttu-id="cf789-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf789-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf789-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf789-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf789-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf789-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf789-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf789-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf789-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf789-119">See Also</span></span>  
 [<span data-ttu-id="cf789-120">Iclrhostbindingpolicymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf789-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="cf789-121">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="cf789-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
