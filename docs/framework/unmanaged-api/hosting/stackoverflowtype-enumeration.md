---
title: StackOverflowType Numaralandırması
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8541ea7b614ff4a6ca666f0e2549a7f50e190192
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135882"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="4218e-102">StackOverflowType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4218e-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="4218e-103">Bir yığın taşması olayı temel nedenini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4218e-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4218e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4218e-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="4218e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4218e-105">Members</span></span>  
  
|<span data-ttu-id="4218e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4218e-106">Member</span></span>|<span data-ttu-id="4218e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4218e-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="4218e-108">Yürütme altyapısı tarafından yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="4218e-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="4218e-109">Yönetilen kod tarafından yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="4218e-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="4218e-110">Tarafından yönetilmeyen kod yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="4218e-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4218e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4218e-111">Remarks</span></span>  
 <span data-ttu-id="4218e-112">Bu bilgiler, ana bilgisayara yapılan bir çağrıyla geçirilir [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4218e-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4218e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4218e-113">Requirements</span></span>  
 <span data-ttu-id="4218e-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4218e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4218e-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4218e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4218e-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4218e-116">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4218e-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4218e-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4218e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4218e-118">See also</span></span>

- [<span data-ttu-id="4218e-119">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="4218e-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
