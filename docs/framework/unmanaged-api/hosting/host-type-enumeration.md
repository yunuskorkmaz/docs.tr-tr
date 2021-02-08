---
description: 'Hakkında daha fazla bilgi edinin: HOST_TYPE numaralandırması'
title: HOST_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: 6a0baf3050f99885953ddec06342cbe19accfef3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785243"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="875f7-103">HOST_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="875f7-103">HOST_TYPE Enumeration</span></span>

<span data-ttu-id="875f7-104">Bir uygulamayı başlatan ana bilgisayar türünü belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="875f7-104">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="875f7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="875f7-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="875f7-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="875f7-106">Members</span></span>  
  
|<span data-ttu-id="875f7-107">Üye</span><span class="sxs-lookup"><span data-stu-id="875f7-107">Member</span></span>|<span data-ttu-id="875f7-108">Description</span><span class="sxs-lookup"><span data-stu-id="875f7-108">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="875f7-109">Uygulamayı AppLaunch.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="875f7-109">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="875f7-110">Kısmen güvenilen uygulamalar için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="875f7-110">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="875f7-111">Uygulamayı doğrudan başlatın.</span><span class="sxs-lookup"><span data-stu-id="875f7-111">Launch the application directly.</span></span> <span data-ttu-id="875f7-112">Diğer bir deyişle, uygulamayı kendi. exe dosyasından başlatın.</span><span class="sxs-lookup"><span data-stu-id="875f7-112">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="875f7-113">Tam güvenilir uygulamalar için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="875f7-113">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="875f7-114">HOST_TYPE_APPLAUNCH ile aynı.</span><span class="sxs-lookup"><span data-stu-id="875f7-114">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="875f7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="875f7-115">Requirements</span></span>  

 <span data-ttu-id="875f7-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="875f7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="875f7-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="875f7-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="875f7-118">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="875f7-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="875f7-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="875f7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875f7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="875f7-120">See also</span></span>

- [<span data-ttu-id="875f7-121">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="875f7-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
