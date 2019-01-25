---
title: EHostBindingPolicyModifyFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3aba84f1ae451ee943028d063e91ca7a6d63548
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504704"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="fd625-102">EHostBindingPolicyModifyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fd625-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="fd625-103">Ortak dil çalışma zamanı (CLR), bir hedef derleme İlkesi değişiklikleri kaynak bütünleştirilmiş koddan uygulama kullanırken gerçekleştirmesi gereken bir yeniden yönlendirme türünü belirtmek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd625-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd625-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd625-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fd625-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fd625-105">Members</span></span>  
  
|<span data-ttu-id="fd625-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fd625-106">Member</span></span>|<span data-ttu-id="fd625-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd625-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="fd625-108">CLR İlkesi değerleri bu hedef bütünleştirilmiş kodun üzerine kaynak derlemenin zincirler belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd625-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="fd625-109">CLR varsayılan eylem gerçekleştirecek belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd625-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="fd625-110">CLR en yüksek değerler için hedef derleme İlkesi değerlerini ayarlayın belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd625-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="fd625-111">CLR ilke değerleri hedef derlemenin kaynak derleme olanlar değiştirecektir belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd625-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd625-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd625-112">Remarks</span></span>  
 <span data-ttu-id="fd625-113">[Iclrhostbindingpolicymanager::modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) yöntemi türünde bir parametre alır `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="fd625-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd625-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd625-114">Requirements</span></span>  
 <span data-ttu-id="fd625-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd625-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd625-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd625-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd625-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd625-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd625-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd625-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd625-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd625-119">See also</span></span>
- [<span data-ttu-id="fd625-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd625-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="fd625-121">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fd625-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
