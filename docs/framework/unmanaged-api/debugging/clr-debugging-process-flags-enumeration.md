---
title: CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8321e5aeba435ca5f1398a9cb827a93ae821d686
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996365"
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="5cefb-102">CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5cefb-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="5cefb-103">Tarafından kullanılan değerleri sağlar [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5cefb-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cefb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cefb-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="5cefb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5cefb-105">Members</span></span>  
  
|<span data-ttu-id="5cefb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5cefb-106">Member</span></span>|<span data-ttu-id="5cefb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cefb-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="5cefb-108">Bu çalışma zamanı göndermek için bir catch yukarı yönetilen hata ayıklayıcı olayında.</span><span class="sxs-lookup"><span data-stu-id="5cefb-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="5cefb-109">Olayları yakalama ve catch yukarı arasındaki fark için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5cefb-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="5cefb-110">Beklemede olan yönetilen olay bir <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> istek.</span><span class="sxs-lookup"><span data-stu-id="5cefb-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cefb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cefb-111">Remarks</span></span>  
 <span data-ttu-id="5cefb-112">Olayları yakalama işlemi, uygulama etki alanı, derleme, modül ve sonra bir işleme eklenmiş kadar geçerli durumu hata ayıklayıcı getiren iş parçacığı oluşturma bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5cefb-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="5cefb-113">Tarafından belirtilen olmayan catch yukarı olayları `CLR_DEBUGGING_MANAGED_EVENT_PENDING` bayrak, tüm diğer hata ayıklayıcı olayları, özel durumlar gibi içerir ve yönetilen hata ayıklama Yardımcısı (MDA) bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="5cefb-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="5cefb-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Bayrağı isteği iptal edilebilir bir yönetilen hata ayıklayıcı ekleyin ve bir sonlandırma özel durumuyla arasında ayırt etmek çalışma zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cefb-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cefb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cefb-115">Requirements</span></span>  
 <span data-ttu-id="5cefb-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cefb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cefb-117">**Üst bilgi:** Metahost.idl, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="5cefb-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="5cefb-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cefb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cefb-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cefb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cefb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cefb-120">See also</span></span>

- [<span data-ttu-id="5cefb-121">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5cefb-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="5cefb-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5cefb-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
