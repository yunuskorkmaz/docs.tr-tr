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
ms.openlocfilehash: 44d5b7fdb2908678671505649bb906c0c5f740e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751137"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="ed53c-102">StackOverflowType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ed53c-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="ed53c-103">Bir yığın taşması olayı temel nedenini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ed53c-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed53c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed53c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="ed53c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ed53c-105">Members</span></span>  
  
|<span data-ttu-id="ed53c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ed53c-106">Member</span></span>|<span data-ttu-id="ed53c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed53c-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="ed53c-108">Yürütme altyapısı tarafından yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="ed53c-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="ed53c-109">Yönetilen kod tarafından yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="ed53c-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="ed53c-110">Tarafından yönetilmeyen kod yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="ed53c-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed53c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed53c-111">Remarks</span></span>  
 <span data-ttu-id="ed53c-112">Bu bilgiler, ana bilgisayara yapılan bir çağrıyla geçirilir [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed53c-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed53c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed53c-113">Requirements</span></span>  
 <span data-ttu-id="ed53c-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed53c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed53c-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed53c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed53c-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed53c-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed53c-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed53c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed53c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed53c-118">See also</span></span>

- [<span data-ttu-id="ed53c-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ed53c-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
