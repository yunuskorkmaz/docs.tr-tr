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
ms.openlocfilehash: dfb1cff3e95c5ff86d22913745b7d14982766b48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968611"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="9acbb-102">HOST_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9acbb-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="9acbb-103">Bir uygulamayı başlatmadan konak türünü belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9acbb-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9acbb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9acbb-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="9acbb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9acbb-105">Members</span></span>  
  
|<span data-ttu-id="9acbb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9acbb-106">Member</span></span>|<span data-ttu-id="9acbb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9acbb-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="9acbb-108">AppLaunch.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="9acbb-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="9acbb-109">Kısmen güvenilen uygulamalar için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9acbb-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="9acbb-110">Uygulamayı doğrudan başlatın.</span><span class="sxs-lookup"><span data-stu-id="9acbb-110">Launch the application directly.</span></span> <span data-ttu-id="9acbb-111">Diğer bir deyişle, kendi .exe dosyası uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="9acbb-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="9acbb-112">Bu değer, tam olarak güvenilen uygulamalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9acbb-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="9acbb-113">HOST_TYPE_APPLAUNCH ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9acbb-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9acbb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9acbb-114">Requirements</span></span>  
 <span data-ttu-id="9acbb-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9acbb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9acbb-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9acbb-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9acbb-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9acbb-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9acbb-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9acbb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acbb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9acbb-119">See also</span></span>

- [<span data-ttu-id="9acbb-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9acbb-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
