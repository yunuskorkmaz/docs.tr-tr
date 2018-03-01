---
title: "StackOverflowType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a04db61a16aeae24476fb0b191a3d2dc89743dee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="8567e-102">StackOverflowType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8567e-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="8567e-103">Bir yığın taşması olayın temel nedenini gösteren değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8567e-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8567e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8567e-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="8567e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8567e-105">Members</span></span>  
  
|<span data-ttu-id="8567e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8567e-106">Member</span></span>|<span data-ttu-id="8567e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8567e-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="8567e-108">Yığın taşması yürütme altyapısı tarafından neden oldu.</span><span class="sxs-lookup"><span data-stu-id="8567e-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="8567e-109">Yığın taşması tarafından yönetilen kod neden oldu.</span><span class="sxs-lookup"><span data-stu-id="8567e-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="8567e-110">Yığın taşması tarafından yönetilmeyen kod neden oldu.</span><span class="sxs-lookup"><span data-stu-id="8567e-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8567e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8567e-111">Remarks</span></span>  
 <span data-ttu-id="8567e-112">Bu bilgiler bir çağrı konağa geçirilir [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8567e-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8567e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8567e-113">Requirements</span></span>  
 <span data-ttu-id="8567e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8567e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8567e-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8567e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8567e-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8567e-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8567e-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8567e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8567e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8567e-118">See Also</span></span>  
 [<span data-ttu-id="8567e-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8567e-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
