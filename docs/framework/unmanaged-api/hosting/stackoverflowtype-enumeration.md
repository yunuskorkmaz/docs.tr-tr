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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777994"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="a9f32-102">StackOverflowType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a9f32-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="a9f32-103">Bir yığın taşması olayı temel nedenini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a9f32-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9f32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9f32-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="a9f32-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a9f32-105">Members</span></span>  
  
|<span data-ttu-id="a9f32-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a9f32-106">Member</span></span>|<span data-ttu-id="a9f32-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9f32-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="a9f32-108">Yürütme altyapısı tarafından yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="a9f32-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="a9f32-109">Yönetilen kod tarafından yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="a9f32-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="a9f32-110">Tarafından yönetilmeyen kod yığın taşmasına neden oldu.</span><span class="sxs-lookup"><span data-stu-id="a9f32-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9f32-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9f32-111">Remarks</span></span>  
 <span data-ttu-id="a9f32-112">Bu bilgiler, ana bilgisayara yapılan bir çağrıyla geçirilir [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a9f32-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9f32-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9f32-113">Requirements</span></span>  
 <span data-ttu-id="a9f32-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9f32-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9f32-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9f32-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9f32-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9f32-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9f32-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9f32-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f32-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9f32-118">See also</span></span>

- [<span data-ttu-id="a9f32-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a9f32-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
