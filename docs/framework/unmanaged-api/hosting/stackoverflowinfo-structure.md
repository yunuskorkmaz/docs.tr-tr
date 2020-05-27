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
ms.openlocfilehash: 941093b9a0856c2b716ba359c854473f3c9ea26a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006525"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="59bff-102">StackOverflowInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="59bff-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="59bff-103">Oluşan taşma türünü ve taşma nedeniyle oluşan özel durum hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="59bff-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59bff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59bff-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="59bff-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="59bff-105">Members</span></span>  
  
|<span data-ttu-id="59bff-106">Üye</span><span class="sxs-lookup"><span data-stu-id="59bff-106">Member</span></span>|<span data-ttu-id="59bff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59bff-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="59bff-108">Taşma türünü belirten [StackOverflowType](stackoverflowtype-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="59bff-108">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="59bff-109">Bir özel durumun `EXCEPTION_POINTERS` makineye bağlı bir açıklamasına sahip bir özel durum kaydı ve özel durum sırasında işlemci bağlamının makineye bağlı açıklamasıyla bir bağlam kaydı Içeren Win32 nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="59bff-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59bff-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59bff-110">Remarks</span></span>  
 <span data-ttu-id="59bff-111">`StackOverflowInfo`Olaylar Için [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) yöntemine bir nesne geçirilir `Event_StackOverflow` .</span><span class="sxs-lookup"><span data-stu-id="59bff-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59bff-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59bff-112">Requirements</span></span>  
 <span data-ttu-id="59bff-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59bff-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59bff-114">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="59bff-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="59bff-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="59bff-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59bff-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59bff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bff-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59bff-117">See also</span></span>

- [<span data-ttu-id="59bff-118">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="59bff-118">Hosting Structures</span></span>](hosting-structures.md)
