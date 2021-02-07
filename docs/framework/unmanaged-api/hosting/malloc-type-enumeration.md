---
description: 'Hakkında daha fazla bilgi edinin: MALLOC_TYPE numaralandırması'
title: MALLOC_TYPE Numaralandırması
ms.date: 03/30/2017
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
ms.openlocfilehash: 47eb58107d79309c34af5f0acdf614804d1f208f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679811"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="0d4de-103">MALLOC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0d4de-103">MALLOC_TYPE Enumeration</span></span>

<span data-ttu-id="0d4de-104">Ayrılmakta olan belleğin özelliklerini belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0d4de-104">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d4de-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d4de-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="0d4de-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0d4de-106">Members</span></span>  
  
|<span data-ttu-id="0d4de-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0d4de-107">Member</span></span>|<span data-ttu-id="0d4de-108">Description</span><span class="sxs-lookup"><span data-stu-id="0d4de-108">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="0d4de-109">Ayrılan bellek yürütülebilir bir dosya içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0d4de-109">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="0d4de-110">Ayrılan bellek, iş parçacığı açısından güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="0d4de-110">The allocated memory is thread-safe.</span></span> <span data-ttu-id="0d4de-111">Diğer bir deyişle, belleğe hiçbir eşitleme olmadan birden çok iş parçacığı tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d4de-111">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="0d4de-112">Bu bayrak ayarlanmamışsa, nesne üzerindeki çağrılar serileştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0d4de-112">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d4de-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d4de-113">Requirements</span></span>  

 <span data-ttu-id="0d4de-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d4de-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d4de-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0d4de-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d4de-116">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d4de-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d4de-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d4de-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4de-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d4de-118">See also</span></span>

- [<span data-ttu-id="0d4de-119">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="0d4de-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
