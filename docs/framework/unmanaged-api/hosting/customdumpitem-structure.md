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
ms.openlocfilehash: 9000f35e9a8f7ecc6c40cf0ef9c220fc9f4f9c10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185932"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="9579b-102">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="9579b-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="9579b-103">Hata Raporlama özel bir döküm eklenmesi için bir öğe açıklar.</span><span class="sxs-lookup"><span data-stu-id="9579b-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9579b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9579b-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="9579b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9579b-105">Members</span></span>  
  
|<span data-ttu-id="9579b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9579b-106">Member</span></span>|<span data-ttu-id="9579b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9579b-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="9579b-108">Bir [Ecustomdumpıtemkind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) eklenecek öğe türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="9579b-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="9579b-109">Şu anda kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="9579b-109">Not currently used.</span></span> <span data-ttu-id="9579b-110">Birleşime eklenen tüm öğeler işaretçi boyutundan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9579b-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="9579b-111">Varsa bir `struct` olan gerekli, ayrı olarak ayırmak ve kendisine işaret.</span><span class="sxs-lookup"><span data-stu-id="9579b-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9579b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9579b-112">Remarks</span></span>  
 <span data-ttu-id="9579b-113">[Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alan `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="9579b-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9579b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9579b-114">Requirements</span></span>  
 <span data-ttu-id="9579b-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9579b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9579b-116">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="9579b-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="9579b-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9579b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9579b-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9579b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9579b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9579b-119">See also</span></span>

- [<span data-ttu-id="9579b-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="9579b-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
