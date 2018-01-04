---
title: "HOST_TYPE Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: HOST_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: HOST_TYPE
helpviewer_keywords: HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8c910dd06109a8a69f29517812737d4b4dcef21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="cb6ff-102">HOST_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cb6ff-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="cb6ff-103">Bir uygulama başlatılmadan ana bilgisayar türünü belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cb6ff-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb6ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb6ff-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="cb6ff-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cb6ff-105">Members</span></span>  
  
|<span data-ttu-id="cb6ff-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cb6ff-106">Member</span></span>|<span data-ttu-id="cb6ff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb6ff-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="cb6ff-108">AppLaunch.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="cb6ff-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="cb6ff-109">Kısmen güvenilir uygulamalar için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb6ff-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="cb6ff-110">Uygulamayı doğrudan başlatın.</span><span class="sxs-lookup"><span data-stu-id="cb6ff-110">Launch the application directly.</span></span> <span data-ttu-id="cb6ff-111">Diğer bir deyişle, kendi .exe dosyası uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="cb6ff-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="cb6ff-112">Bu değeri tam olarak güvenilir uygulamalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb6ff-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="cb6ff-113">HOST_TYPE_APPLAUNCH ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cb6ff-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb6ff-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb6ff-114">Requirements</span></span>  
 <span data-ttu-id="cb6ff-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb6ff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb6ff-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb6ff-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb6ff-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb6ff-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb6ff-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb6ff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6ff-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb6ff-119">See Also</span></span>  
 [<span data-ttu-id="cb6ff-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cb6ff-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
