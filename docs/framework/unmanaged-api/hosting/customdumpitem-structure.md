---
title: CustomDumpItem Yapısı
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616443"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="55ce9-102">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="55ce9-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="55ce9-103">Hata raporlamada özel bir döküme eklenecek bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55ce9-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55ce9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="55ce9-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="55ce9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="55ce9-105">Members</span></span>  
  
|<span data-ttu-id="55ce9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="55ce9-106">Member</span></span>|<span data-ttu-id="55ce9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55ce9-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="55ce9-108">Eklenecek öğe türünü gösteren bir [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="55ce9-108">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="55ce9-109">Şu anda kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="55ce9-109">Not currently used.</span></span> <span data-ttu-id="55ce9-110">Birleşime eklenen öğelerin işaretçi boyutundan büyük olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="55ce9-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="55ce9-111">Bir `struct` gerekliyse, onu ayrı olarak ayırmanız ve üzerine işaret etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="55ce9-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55ce9-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55ce9-112">Remarks</span></span>  
 <span data-ttu-id="55ce9-113">[ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alır `CustomDumpItem` .</span><span class="sxs-lookup"><span data-stu-id="55ce9-113">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55ce9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55ce9-114">Requirements</span></span>  
 <span data-ttu-id="55ce9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55ce9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55ce9-116">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="55ce9-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="55ce9-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="55ce9-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55ce9-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55ce9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ce9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55ce9-119">See also</span></span>

- [<span data-ttu-id="55ce9-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="55ce9-120">Hosting Structures</span></span>](hosting-structures.md)
