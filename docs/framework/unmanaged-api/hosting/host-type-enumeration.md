---
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
ms.openlocfilehash: e8dda83df8a320733f45dbcc13599cdf37d26492
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617158"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="895d1-102">HOST_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="895d1-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="895d1-103">Bir uygulamayı başlatan ana bilgisayar türünü belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="895d1-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="895d1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="895d1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="895d1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="895d1-105">Members</span></span>  
  
|<span data-ttu-id="895d1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="895d1-106">Member</span></span>|<span data-ttu-id="895d1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="895d1-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="895d1-108">Uygulamayı Applalaunch. exe ' den başlatın.</span><span class="sxs-lookup"><span data-stu-id="895d1-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="895d1-109">Kısmen güvenilen uygulamalar için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="895d1-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="895d1-110">Uygulamayı doğrudan başlatın.</span><span class="sxs-lookup"><span data-stu-id="895d1-110">Launch the application directly.</span></span> <span data-ttu-id="895d1-111">Diğer bir deyişle, uygulamayı kendi. exe dosyasından başlatın.</span><span class="sxs-lookup"><span data-stu-id="895d1-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="895d1-112">Tam güvenilir uygulamalar için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="895d1-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="895d1-113">HOST_TYPE_APPLAUNCH ile aynı.</span><span class="sxs-lookup"><span data-stu-id="895d1-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="895d1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="895d1-114">Requirements</span></span>  
 <span data-ttu-id="895d1-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="895d1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="895d1-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="895d1-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="895d1-117">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="895d1-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="895d1-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="895d1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895d1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="895d1-119">See also</span></span>

- [<span data-ttu-id="895d1-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="895d1-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
