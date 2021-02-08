---
description: ': EHostBindingPolicyModifyFlags numaralandırması hakkında daha fazla bilgi'
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
ms.openlocfilehash: be8a15cad49097d1ea2e206e01da2d5d5dcb165a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785490"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="19112-103">EHostBindingPolicyModifyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="19112-103">EHostBindingPolicyModifyFlags Enumeration</span></span>

<span data-ttu-id="19112-104">Ana bilgisayarın bir kaynak derlemeden hedef derlemeye ilke değişiklikleri uygularken gerçekleştirmesi gereken ortak dil çalışma zamanının (CLR) yeniden yönlendirme türünü belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19112-104">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19112-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="19112-105">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="19112-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="19112-106">Members</span></span>  
  
|<span data-ttu-id="19112-107">Üye</span><span class="sxs-lookup"><span data-stu-id="19112-107">Member</span></span>|<span data-ttu-id="19112-108">Description</span><span class="sxs-lookup"><span data-stu-id="19112-108">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="19112-109">CLR 'nin, kaynak derlemenin ilke değerlerini hedef derlemeye göre zincirlemesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19112-109">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="19112-110">CLR 'nin varsayılan eylemi gerçekleştireceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19112-110">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="19112-111">CLR 'nin hedef derlemenin ilke değerlerini en fazla değere ayarlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="19112-111">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="19112-112">CLR 'nin hedef derlemenin ilke değerlerini kaynak derlemeden değiştirecek şekilde değiştirmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19112-112">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19112-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19112-113">Remarks</span></span>  

 <span data-ttu-id="19112-114">[ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) yöntemi türünde bir parametre alır `EHostBindingPolicyModifyFlags` .</span><span class="sxs-lookup"><span data-stu-id="19112-114">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19112-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19112-115">Requirements</span></span>  

 <span data-ttu-id="19112-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19112-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19112-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19112-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19112-118">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19112-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19112-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19112-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19112-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19112-120">See also</span></span>

- [<span data-ttu-id="19112-121">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19112-121">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="19112-122">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="19112-122">Hosting Enumerations</span></span>](hosting-enumerations.md)
