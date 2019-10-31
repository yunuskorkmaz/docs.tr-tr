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
ms.openlocfilehash: 1072026f92edbc646653c6dd74ec8e22d5b887e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105913"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="495ee-102">StackOverflowInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="495ee-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="495ee-103">Oluşan taşma türünü ve taşma nedeniyle oluşan özel durum hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="495ee-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="495ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="495ee-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="495ee-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="495ee-105">Members</span></span>  
  
|<span data-ttu-id="495ee-106">Üye</span><span class="sxs-lookup"><span data-stu-id="495ee-106">Member</span></span>|<span data-ttu-id="495ee-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="495ee-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="495ee-108">Taşma türünü belirten [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="495ee-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="495ee-109">Bir özel durumun makineye bağlı açıklamasıyla bir özel durum kaydı ve özel durum sırasında işlemci bağlamının makineye bağlı açıklamasıyla bir bağlam kaydı içeren Win32 `EXCEPTION_POINTERS` nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="495ee-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="495ee-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="495ee-110">Remarks</span></span>  
 <span data-ttu-id="495ee-111">`StackOverflowInfo` nesnesi, `Event_StackOverflow` olayları için [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="495ee-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="495ee-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="495ee-112">Requirements</span></span>  
 <span data-ttu-id="495ee-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="495ee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="495ee-114">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="495ee-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="495ee-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="495ee-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="495ee-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="495ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495ee-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="495ee-117">See also</span></span>

- [<span data-ttu-id="495ee-118">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="495ee-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
