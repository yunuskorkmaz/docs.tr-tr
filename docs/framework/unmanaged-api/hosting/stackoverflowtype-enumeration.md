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
ms.openlocfilehash: 06c9119a2b842a0efcd4af752ba72dbfda03bf13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653872"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="32bab-102">StackOverflowType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="32bab-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="32bab-103">Bir yığın taşması olayı temel nedenini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="32bab-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32bab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32bab-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="32bab-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="32bab-105">Members</span></span>  
  
|<span data-ttu-id="32bab-106">Üye</span><span class="sxs-lookup"><span data-stu-id="32bab-106">Member</span></span>|<span data-ttu-id="32bab-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32bab-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="32bab-108">Yürütme altyapısı tarafından yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="32bab-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="32bab-109">Yönetilen kod tarafından yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="32bab-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="32bab-110">Tarafından yönetilmeyen kod yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="32bab-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32bab-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32bab-111">Remarks</span></span>  
 <span data-ttu-id="32bab-112">Bu bilgiler, ana bilgisayara yapılan bir çağrıyla geçirilir [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32bab-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32bab-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32bab-113">Requirements</span></span>  
 <span data-ttu-id="32bab-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32bab-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32bab-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32bab-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32bab-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32bab-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32bab-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32bab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bab-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32bab-118">See also</span></span>
- [<span data-ttu-id="32bab-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="32bab-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
