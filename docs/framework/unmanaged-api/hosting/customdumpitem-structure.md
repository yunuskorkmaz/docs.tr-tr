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
ms.openlocfilehash: ae64edd8a3a628100d4c51d0b78be1bc8d49fc17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138280"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="3012a-102">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="3012a-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="3012a-103">Hata raporlamada özel bir döküme eklenecek bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3012a-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3012a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3012a-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="3012a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3012a-105">Members</span></span>  
  
|<span data-ttu-id="3012a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3012a-106">Member</span></span>|<span data-ttu-id="3012a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3012a-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="3012a-108">Eklenecek öğe türünü gösteren bir [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="3012a-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="3012a-109">Şu anda kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3012a-109">Not currently used.</span></span> <span data-ttu-id="3012a-110">Birleşime eklenen öğelerin işaretçi boyutundan büyük olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3012a-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="3012a-111">Bir `struct` gerekiyorsa, bunu ayrı olarak ayırmanız ve üzerine işaret etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3012a-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3012a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3012a-112">Remarks</span></span>  
 <span data-ttu-id="3012a-113">[ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) , `CustomDumpItem`türünde bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="3012a-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3012a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3012a-114">Requirements</span></span>  
 <span data-ttu-id="3012a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3012a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3012a-116">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="3012a-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="3012a-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3012a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3012a-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3012a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3012a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3012a-119">See also</span></span>

- [<span data-ttu-id="3012a-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="3012a-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
