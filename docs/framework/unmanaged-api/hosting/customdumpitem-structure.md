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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05f5d3fbe05ad1e97a1ae61ed0496f314c4ec5cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765960"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="1d036-102">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="1d036-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="1d036-103">Hata Raporlama özel bir döküm eklenmesi için bir öğe açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d036-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d036-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d036-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="1d036-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1d036-105">Members</span></span>  
  
|<span data-ttu-id="1d036-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1d036-106">Member</span></span>|<span data-ttu-id="1d036-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d036-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="1d036-108">Bir [Ecustomdumpıtemkind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) eklenecek öğe türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1d036-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="1d036-109">Şu anda kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="1d036-109">Not currently used.</span></span> <span data-ttu-id="1d036-110">Birleşime eklenen tüm öğeler işaretçi boyutundan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d036-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="1d036-111">Varsa bir `struct` olan gerekli, ayrı olarak ayırmak ve kendisine işaret.</span><span class="sxs-lookup"><span data-stu-id="1d036-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d036-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d036-112">Remarks</span></span>  
 <span data-ttu-id="1d036-113">[Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alan `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="1d036-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d036-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d036-114">Requirements</span></span>  
 <span data-ttu-id="1d036-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d036-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d036-116">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="1d036-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="1d036-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1d036-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d036-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d036-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d036-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d036-119">See also</span></span>

- [<span data-ttu-id="1d036-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="1d036-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
