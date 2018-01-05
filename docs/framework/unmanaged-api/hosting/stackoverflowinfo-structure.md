---
title: "StackOverflowInfo Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowInfo
helpviewer_keywords: StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a880a7c30277d382bff2b46ebe10720880e907
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="d772e-102">StackOverflowInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="d772e-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="d772e-103">Taşması nedeniyle atılan özel durum oluştu Taşması ve bilgi türünü saklar.</span><span class="sxs-lookup"><span data-stu-id="d772e-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d772e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d772e-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="d772e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d772e-105">Members</span></span>  
  
|<span data-ttu-id="d772e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d772e-106">Member</span></span>|<span data-ttu-id="d772e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d772e-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="d772e-108">Değerini [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) numaralandırma taşma türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d772e-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="d772e-109">Bir işaretçi bir Win32 `EXCEPTION_POINTERS` makine bağımsız açıklamasını bir özel durum ile bir özel durum kaydı ve makine bağımlı açıklamasını işlemci bağlamı özel durumu zaman bağlam kaydıyla içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="d772e-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d772e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d772e-110">Remarks</span></span>  
 <span data-ttu-id="d772e-111">A `StackOverflowInfo` nesne iletilir [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi `Event_StackOverflow` olaylar.</span><span class="sxs-lookup"><span data-stu-id="d772e-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d772e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d772e-112">Requirements</span></span>  
 <span data-ttu-id="d772e-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d772e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d772e-114">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="d772e-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d772e-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d772e-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d772e-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d772e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d772e-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d772e-117">See Also</span></span>  
 [<span data-ttu-id="d772e-118">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="d772e-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
