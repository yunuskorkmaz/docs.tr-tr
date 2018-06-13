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
ms.openlocfilehash: 9e888b2359336c68ea6fdf52f798145fda12002e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440875"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="d4d56-102">StackOverflowType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d4d56-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="d4d56-103">Bir yığın taşması olayın temel nedenini gösteren değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d4d56-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4d56-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="d4d56-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d4d56-105">Members</span></span>  
  
|<span data-ttu-id="d4d56-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d4d56-106">Member</span></span>|<span data-ttu-id="d4d56-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4d56-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="d4d56-108">Yığın taşması yürütme altyapısı tarafından neden oldu.</span><span class="sxs-lookup"><span data-stu-id="d4d56-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="d4d56-109">Yığın taşması tarafından yönetilen kod neden oldu.</span><span class="sxs-lookup"><span data-stu-id="d4d56-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="d4d56-110">Yığın taşması tarafından yönetilmeyen kod neden oldu.</span><span class="sxs-lookup"><span data-stu-id="d4d56-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4d56-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4d56-111">Remarks</span></span>  
 <span data-ttu-id="d4d56-112">Bu bilgiler bir çağrı konağa geçirilir [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d4d56-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d56-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4d56-113">Requirements</span></span>  
 <span data-ttu-id="d4d56-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4d56-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d56-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4d56-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4d56-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4d56-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4d56-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d56-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4d56-118">See Also</span></span>  
 [<span data-ttu-id="d4d56-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d4d56-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
