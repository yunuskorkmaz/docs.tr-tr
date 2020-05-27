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
ms.openlocfilehash: f399d33dbe05cb5768aa45533ef30d28409e18e2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006486"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="e37ce-102">StackOverflowType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e37ce-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="e37ce-103">Yığın taşması olayının temel nedenini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e37ce-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e37ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e37ce-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="e37ce-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e37ce-105">Members</span></span>  
  
|<span data-ttu-id="e37ce-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e37ce-106">Member</span></span>|<span data-ttu-id="e37ce-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e37ce-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="e37ce-108">Yığın taşması yürütme altyapısından kaynaklandı.</span><span class="sxs-lookup"><span data-stu-id="e37ce-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="e37ce-109">Yönetilen koddan oluşan yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="e37ce-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="e37ce-110">Yığın taşması, yönetilmeyen koddan kaynaklandı.</span><span class="sxs-lookup"><span data-stu-id="e37ce-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e37ce-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e37ce-111">Remarks</span></span>  
 <span data-ttu-id="e37ce-112">Bu bilgiler, [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) yöntemine yapılan bir çağrı aracılığıyla konağa geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e37ce-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e37ce-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e37ce-113">Requirements</span></span>  
 <span data-ttu-id="e37ce-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e37ce-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e37ce-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e37ce-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e37ce-116">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e37ce-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e37ce-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e37ce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37ce-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e37ce-118">See also</span></span>

- [<span data-ttu-id="e37ce-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e37ce-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
