---
title: StackOverflowInfo Yapısı
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac0f5d522a24394369583692f8c564254529bf13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137357"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="87256-102">StackOverflowInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="87256-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="87256-103">Taşması nedeniyle oluşturulan özel durum oluştu taşma ve bilgi türünü saklar.</span><span class="sxs-lookup"><span data-stu-id="87256-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87256-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87256-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="87256-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="87256-105">Members</span></span>  
  
|<span data-ttu-id="87256-106">Üye</span><span class="sxs-lookup"><span data-stu-id="87256-106">Member</span></span>|<span data-ttu-id="87256-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87256-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="87256-108">Değerini [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) taşma türünü belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="87256-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="87256-109">Bir Win32 işaretçisi `EXCEPTION_POINTERS` bir özel durum makine bağımsız açıklamasını içeren bir özel durum kaydını ve özel durumun zaman makine bağımlı bir işlemci bağlamı açıklamasını içeren bir bağlam kaydı içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="87256-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87256-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87256-110">Remarks</span></span>  
 <span data-ttu-id="87256-111">A `StackOverflowInfo` nesnesi [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi `Event_StackOverflow` olayları.</span><span class="sxs-lookup"><span data-stu-id="87256-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87256-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87256-112">Requirements</span></span>  
 <span data-ttu-id="87256-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87256-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87256-114">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="87256-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="87256-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="87256-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87256-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87256-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87256-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87256-117">See also</span></span>

- [<span data-ttu-id="87256-118">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="87256-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
