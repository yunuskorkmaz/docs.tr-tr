---
description: 'Daha fazla bilgi edinin: StackOverflowInfo yapısı'
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
ms.openlocfilehash: cca65e4293c05b89ebefc3c6dd36a6b8898eb15f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679400"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="18676-103">StackOverflowInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="18676-103">StackOverflowInfo Structure</span></span>

<span data-ttu-id="18676-104">Oluşan taşma türünü ve taşma nedeniyle oluşan özel durum hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="18676-104">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18676-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="18676-105">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="18676-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="18676-106">Members</span></span>  
  
|<span data-ttu-id="18676-107">Üye</span><span class="sxs-lookup"><span data-stu-id="18676-107">Member</span></span>|<span data-ttu-id="18676-108">Description</span><span class="sxs-lookup"><span data-stu-id="18676-108">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="18676-109">Taşma türünü belirten [StackOverflowType](stackoverflowtype-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="18676-109">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="18676-110">Bir özel durumun `EXCEPTION_POINTERS` makineye bağlı bir açıklamasına sahip bir özel durum kaydı ve özel durum sırasında işlemci bağlamının makineye bağlı açıklamasıyla bir bağlam kaydı Içeren Win32 nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18676-110">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18676-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18676-111">Remarks</span></span>  

 <span data-ttu-id="18676-112">`StackOverflowInfo`Olaylar Için [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) yöntemine bir nesne geçirilir `Event_StackOverflow` .</span><span class="sxs-lookup"><span data-stu-id="18676-112">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18676-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18676-113">Requirements</span></span>  

 <span data-ttu-id="18676-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18676-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18676-115">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="18676-115">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="18676-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="18676-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18676-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18676-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18676-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18676-118">See also</span></span>

- [<span data-ttu-id="18676-119">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="18676-119">Hosting Structures</span></span>](hosting-structures.md)
