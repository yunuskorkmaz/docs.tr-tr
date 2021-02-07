---
description: 'Hakkında daha fazla bilgi edinin: StackOverflowType numaralandırması'
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
ms.openlocfilehash: d39ccd99331a3e839236f1ede21254edb92b2dfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679374"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="a62d4-103">StackOverflowType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a62d4-103">StackOverflowType Enumeration</span></span>

<span data-ttu-id="a62d4-104">Yığın taşması olayının temel nedenini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a62d4-104">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a62d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a62d4-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="a62d4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a62d4-106">Members</span></span>  
  
|<span data-ttu-id="a62d4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a62d4-107">Member</span></span>|<span data-ttu-id="a62d4-108">Description</span><span class="sxs-lookup"><span data-stu-id="a62d4-108">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="a62d4-109">Yığın taşması yürütme altyapısından kaynaklandı.</span><span class="sxs-lookup"><span data-stu-id="a62d4-109">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="a62d4-110">Yönetilen koddan oluşan yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="a62d4-110">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="a62d4-111">Yığın taşması, yönetilmeyen koddan kaynaklandı.</span><span class="sxs-lookup"><span data-stu-id="a62d4-111">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a62d4-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a62d4-112">Remarks</span></span>  

 <span data-ttu-id="a62d4-113">Bu bilgiler, [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) yöntemine yapılan bir çağrı aracılığıyla konağa geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a62d4-113">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a62d4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a62d4-114">Requirements</span></span>  

 <span data-ttu-id="a62d4-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a62d4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a62d4-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a62d4-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a62d4-117">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a62d4-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a62d4-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a62d4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62d4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a62d4-119">See also</span></span>

- [<span data-ttu-id="a62d4-120">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a62d4-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
