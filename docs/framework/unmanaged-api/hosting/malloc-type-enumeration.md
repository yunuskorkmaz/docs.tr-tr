---
title: "MALLOC_TYPE Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3f41f381266c76b267d5d3e366047fe5267c30b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="a461f-102">MALLOC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a461f-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="a461f-103">Ayrılan bellek özelliklerini belirtin değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a461f-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a461f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a461f-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="a461f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a461f-105">Members</span></span>  
  
|<span data-ttu-id="a461f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a461f-106">Member</span></span>|<span data-ttu-id="a461f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a461f-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="a461f-108">Ayrılmış bellek yürütülebilir bir dosyanın içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a461f-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="a461f-109">Ayrılmış bellek iş parçacığı güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="a461f-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="a461f-110">Diğer bir deyişle, bellek, herhangi bir eşitleme olmadan birden çok iş parçacığı tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a461f-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="a461f-111">Bu bayrak ayarlanmazsa, nesne üzerinde çağrıları seri hale getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a461f-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a461f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a461f-112">Requirements</span></span>  
 <span data-ttu-id="a461f-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a461f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a461f-114">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a461f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a461f-115">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a461f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a461f-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a461f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a461f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a461f-117">See Also</span></span>  
 [<span data-ttu-id="a461f-118">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a461f-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
