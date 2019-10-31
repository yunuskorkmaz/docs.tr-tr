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
ms.openlocfilehash: 16f56809b4db159c71b06b3bb9d969f8a8f8fc54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090831"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="6496a-102">MALLOC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6496a-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="6496a-103">Ayrılmakta olan belleğin özelliklerini belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6496a-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6496a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6496a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="6496a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6496a-105">Members</span></span>  
  
|<span data-ttu-id="6496a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6496a-106">Member</span></span>|<span data-ttu-id="6496a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6496a-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="6496a-108">Ayrılan bellek yürütülebilir bir dosya içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6496a-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="6496a-109">Ayrılan bellek, iş parçacığı açısından güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="6496a-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="6496a-110">Diğer bir deyişle, belleğe hiçbir eşitleme olmadan birden çok iş parçacığı tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6496a-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="6496a-111">Bu bayrak ayarlanmamışsa, nesne üzerindeki çağrılar serileştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6496a-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6496a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6496a-112">Requirements</span></span>  
 <span data-ttu-id="6496a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6496a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6496a-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6496a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6496a-115">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6496a-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6496a-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6496a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6496a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6496a-117">See also</span></span>

- [<span data-ttu-id="6496a-118">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6496a-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
