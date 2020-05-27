---
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
ms.openlocfilehash: 630fe4e79b369bfdefc19be72780f1893090895e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008462"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="6e7ee-102">MALLOC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6e7ee-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="6e7ee-103">Ayrılmakta olan belleğin özelliklerini belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6e7ee-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e7ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e7ee-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="6e7ee-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6e7ee-105">Members</span></span>  
  
|<span data-ttu-id="6e7ee-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6e7ee-106">Member</span></span>|<span data-ttu-id="6e7ee-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e7ee-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="6e7ee-108">Ayrılan bellek yürütülebilir bir dosya içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6e7ee-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="6e7ee-109">Ayrılan bellek, iş parçacığı açısından güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="6e7ee-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="6e7ee-110">Diğer bir deyişle, belleğe hiçbir eşitleme olmadan birden çok iş parçacığı tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6e7ee-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="6e7ee-111">Bu bayrak ayarlanmamışsa, nesne üzerindeki çağrılar serileştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6e7ee-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e7ee-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e7ee-112">Requirements</span></span>  
 <span data-ttu-id="6e7ee-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e7ee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e7ee-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6e7ee-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e7ee-115">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6e7ee-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e7ee-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e7ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7ee-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e7ee-117">See also</span></span>

- [<span data-ttu-id="6e7ee-118">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6e7ee-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
