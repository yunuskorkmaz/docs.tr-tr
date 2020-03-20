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
ms.openlocfilehash: 154beef9398029f31dcb4d081019b9f292238af4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176480"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="f9a7f-102">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="f9a7f-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="f9a7f-103">Hata bildiriminde özel bir döküme eklenecek bir öğeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9a7f-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a7f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9a7f-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="f9a7f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f9a7f-105">Members</span></span>  
  
|<span data-ttu-id="f9a7f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f9a7f-106">Member</span></span>|<span data-ttu-id="f9a7f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9a7f-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="f9a7f-108">Eklenecek öğe türünü gösteren [bir ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="f9a7f-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="f9a7f-109">Şu anda kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f9a7f-109">Not currently used.</span></span> <span data-ttu-id="f9a7f-110">Birliğe eklenen öğeler işaretçi boyutundan büyük olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9a7f-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="f9a7f-111">A `struct` gerekiyorsa, ayrı ayrı ayırmanız ve işaret etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9a7f-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9a7f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9a7f-112">Remarks</span></span>  
 <span data-ttu-id="f9a7f-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) türünden `CustomDumpItem`bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="f9a7f-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9a7f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9a7f-114">Requirements</span></span>  
 <span data-ttu-id="f9a7f-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9a7f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a7f-116">**Üstbilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="f9a7f-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f9a7f-117">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="f9a7f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9a7f-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a7f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a7f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9a7f-119">See also</span></span>

- [<span data-ttu-id="f9a7f-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="f9a7f-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
