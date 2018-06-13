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
ms.openlocfilehash: f742d219d603488bbade091f7a8192785d3e84f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433102"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="22a02-102">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="22a02-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="22a02-103">Hata Raporlama özel bir döküm eklenmesi için bir öğe açıklar.</span><span class="sxs-lookup"><span data-stu-id="22a02-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a02-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22a02-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="22a02-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="22a02-105">Members</span></span>  
  
|<span data-ttu-id="22a02-106">Üye</span><span class="sxs-lookup"><span data-stu-id="22a02-106">Member</span></span>|<span data-ttu-id="22a02-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22a02-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="22a02-108">Bir [Ecustomdumpıtemkind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) eklenecek öğe türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="22a02-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="22a02-109">Şu anda kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="22a02-109">Not currently used.</span></span> <span data-ttu-id="22a02-110">UNION eklenen tüm öğeler işaretçi boyutundan daha büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22a02-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="22a02-111">Varsa bir `struct` olan gerekli, ayrı ayrı ayırın ve gerekir kendisine noktası.</span><span class="sxs-lookup"><span data-stu-id="22a02-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22a02-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22a02-112">Remarks</span></span>  
 <span data-ttu-id="22a02-113">[Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alan `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="22a02-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22a02-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22a02-114">Requirements</span></span>  
 <span data-ttu-id="22a02-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22a02-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a02-116">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="22a02-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="22a02-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="22a02-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22a02-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22a02-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a02-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22a02-119">See Also</span></span>  
 [<span data-ttu-id="22a02-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="22a02-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
