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
ms.openlocfilehash: 0e8357d20edba993f5a7682f31c04afea4362afd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080221"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="1e9c8-102">EHostBindingPolicyModifyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1e9c8-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="1e9c8-103">Ortak dil çalışma zamanı (CLR), bir hedef derleme İlkesi değişiklikleri kaynak bütünleştirilmiş koddan uygulama kullanırken gerçekleştirmesi gereken bir yeniden yönlendirme türünü belirtmek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e9c8-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e9c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e9c8-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="1e9c8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1e9c8-105">Members</span></span>  
  
|<span data-ttu-id="1e9c8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1e9c8-106">Member</span></span>|<span data-ttu-id="1e9c8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e9c8-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="1e9c8-108">CLR İlkesi değerleri bu hedef bütünleştirilmiş kodun üzerine kaynak derlemenin zincirler belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e9c8-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="1e9c8-109">CLR varsayılan eylem gerçekleştirecek belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e9c8-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="1e9c8-110">CLR en yüksek değerler için hedef derleme İlkesi değerlerini ayarlayın belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e9c8-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="1e9c8-111">CLR ilke değerleri hedef derlemenin kaynak derleme olanlar değiştirecektir belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e9c8-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e9c8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e9c8-112">Remarks</span></span>  
 <span data-ttu-id="1e9c8-113">[Iclrhostbindingpolicymanager::modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) yöntemi türünde bir parametre alır `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="1e9c8-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e9c8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e9c8-114">Requirements</span></span>  
 <span data-ttu-id="1e9c8-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e9c8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e9c8-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e9c8-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e9c8-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e9c8-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e9c8-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e9c8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9c8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e9c8-119">See also</span></span>

- [<span data-ttu-id="1e9c8-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e9c8-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="1e9c8-121">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="1e9c8-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
