---
description: 'Daha fazla bilgi edinin: CustomDumpItem yapısı'
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
ms.openlocfilehash: 9bd7b2bb59675bc01e24dc6e6d0ce524f3d35466
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716906"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="0c8d4-103">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="0c8d4-103">CustomDumpItem Structure</span></span>

<span data-ttu-id="0c8d4-104">Hata raporlamada özel bir döküme eklenecek bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0c8d4-104">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c8d4-105">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="0c8d4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0c8d4-106">Members</span></span>  
  
|<span data-ttu-id="0c8d4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0c8d4-107">Member</span></span>|<span data-ttu-id="0c8d4-108">Description</span><span class="sxs-lookup"><span data-stu-id="0c8d4-108">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="0c8d4-109">Eklenecek öğe türünü gösteren bir [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="0c8d4-109">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="0c8d4-110">Şu anda kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0c8d4-110">Not currently used.</span></span> <span data-ttu-id="0c8d4-111">Birleşime eklenen öğelerin işaretçi boyutundan büyük olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c8d4-111">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="0c8d4-112">Bir `struct` gerekliyse, onu ayrı olarak ayırmanız ve üzerine işaret etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c8d4-112">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c8d4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c8d4-113">Remarks</span></span>  

 <span data-ttu-id="0c8d4-114">[ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alır `CustomDumpItem` .</span><span class="sxs-lookup"><span data-stu-id="0c8d4-114">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8d4-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c8d4-115">Requirements</span></span>  

 <span data-ttu-id="0c8d4-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8d4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8d4-117">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="0c8d4-117">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0c8d4-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0c8d4-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c8d4-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8d4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8d4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c8d4-120">See also</span></span>

- [<span data-ttu-id="0c8d4-121">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="0c8d4-121">Hosting Structures</span></span>](hosting-structures.md)
