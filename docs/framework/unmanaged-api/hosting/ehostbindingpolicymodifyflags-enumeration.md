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
ms.openlocfilehash: 256c362ae0aea51fea16ce799db243b105dee81a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616248"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="fcdf8-102">EHostBindingPolicyModifyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fcdf8-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="fcdf8-103">Ana bilgisayarın bir kaynak derlemeden hedef derlemeye ilke değişiklikleri uygularken gerçekleştirmesi gereken ortak dil çalışma zamanının (CLR) yeniden yönlendirme türünü belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcdf8-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcdf8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fcdf8-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fcdf8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fcdf8-105">Members</span></span>  
  
|<span data-ttu-id="fcdf8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fcdf8-106">Member</span></span>|<span data-ttu-id="fcdf8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcdf8-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="fcdf8-108">CLR 'nin, kaynak derlemenin ilke değerlerini hedef derlemeye göre zincirlemesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcdf8-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="fcdf8-109">CLR 'nin varsayılan eylemi gerçekleştireceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcdf8-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="fcdf8-110">CLR 'nin hedef derlemenin ilke değerlerini en fazla değere ayarlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fcdf8-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="fcdf8-111">CLR 'nin hedef derlemenin ilke değerlerini kaynak derlemeden değiştirecek şekilde değiştirmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcdf8-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcdf8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcdf8-112">Remarks</span></span>  
 <span data-ttu-id="fcdf8-113">[ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) yöntemi türünde bir parametre alır `EHostBindingPolicyModifyFlags` .</span><span class="sxs-lookup"><span data-stu-id="fcdf8-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcdf8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcdf8-114">Requirements</span></span>  
 <span data-ttu-id="fcdf8-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcdf8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcdf8-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fcdf8-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fcdf8-117">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fcdf8-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcdf8-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcdf8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdf8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcdf8-119">See also</span></span>

- [<span data-ttu-id="fcdf8-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcdf8-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="fcdf8-121">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fcdf8-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
