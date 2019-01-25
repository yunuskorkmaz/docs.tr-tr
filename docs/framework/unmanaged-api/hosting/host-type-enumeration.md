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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a2db1aea04ae060623bc39a52ed6990f6137f82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606458"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="3ddd3-102">HOST_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3ddd3-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="3ddd3-103">Bir uygulamayı başlatmadan konak türünü belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3ddd3-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ddd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ddd3-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="3ddd3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3ddd3-105">Members</span></span>  
  
|<span data-ttu-id="3ddd3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3ddd3-106">Member</span></span>|<span data-ttu-id="3ddd3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ddd3-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="3ddd3-108">AppLaunch.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="3ddd3-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="3ddd3-109">Kısmen güvenilen uygulamalar için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ddd3-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="3ddd3-110">Uygulamayı doğrudan başlatın.</span><span class="sxs-lookup"><span data-stu-id="3ddd3-110">Launch the application directly.</span></span> <span data-ttu-id="3ddd3-111">Diğer bir deyişle, kendi .exe dosyası uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="3ddd3-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="3ddd3-112">Bu değer, tam olarak güvenilen uygulamalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ddd3-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="3ddd3-113">HOST_TYPE_APPLAUNCH ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3ddd3-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ddd3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ddd3-114">Requirements</span></span>  
 <span data-ttu-id="3ddd3-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ddd3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ddd3-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3ddd3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ddd3-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ddd3-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ddd3-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ddd3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ddd3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ddd3-119">See also</span></span>
- [<span data-ttu-id="3ddd3-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3ddd3-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
