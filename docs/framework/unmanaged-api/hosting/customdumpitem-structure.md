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
ms.openlocfilehash: c77e93686c7d121e9fe2a92f03970404ab823dc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673247"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="7e318-102">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="7e318-102">CustomDumpItem Structure</span></span>

<span data-ttu-id="7e318-103">Hata raporlamada özel bir döküme eklenecek bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e318-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e318-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e318-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="7e318-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7e318-105">Members</span></span>  
  
|<span data-ttu-id="7e318-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7e318-106">Member</span></span>|<span data-ttu-id="7e318-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e318-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="7e318-108">Eklenecek öğe türünü gösteren bir [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="7e318-108">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="7e318-109">Şu anda kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7e318-109">Not currently used.</span></span> <span data-ttu-id="7e318-110">Birleşime eklenen öğelerin işaretçi boyutundan büyük olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e318-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="7e318-111">Bir `struct` gerekliyse, onu ayrı olarak ayırmanız ve üzerine işaret etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e318-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e318-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e318-112">Remarks</span></span>  

 <span data-ttu-id="7e318-113">[ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alır `CustomDumpItem` .</span><span class="sxs-lookup"><span data-stu-id="7e318-113">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e318-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e318-114">Requirements</span></span>  

 <span data-ttu-id="7e318-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e318-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e318-116">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="7e318-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7e318-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7e318-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e318-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e318-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e318-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e318-119">See also</span></span>

- [<span data-ttu-id="7e318-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="7e318-120">Hosting Structures</span></span>](hosting-structures.md)
