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
ms.openlocfilehash: caf76fa7962de9392b06591777ac862aa548d20d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779545"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="d75a9-102">HOST_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d75a9-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="d75a9-103">Bir uygulamayı başlatmadan konak türünü belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d75a9-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d75a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d75a9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="d75a9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d75a9-105">Members</span></span>  
  
|<span data-ttu-id="d75a9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d75a9-106">Member</span></span>|<span data-ttu-id="d75a9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d75a9-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="d75a9-108">AppLaunch.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="d75a9-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="d75a9-109">Kısmen güvenilen uygulamalar için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d75a9-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="d75a9-110">Uygulamayı doğrudan başlatın.</span><span class="sxs-lookup"><span data-stu-id="d75a9-110">Launch the application directly.</span></span> <span data-ttu-id="d75a9-111">Diğer bir deyişle, kendi .exe dosyası uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="d75a9-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="d75a9-112">Bu değer, tam olarak güvenilen uygulamalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d75a9-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="d75a9-113">HOST_TYPE_APPLAUNCH ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d75a9-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d75a9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d75a9-114">Requirements</span></span>  
 <span data-ttu-id="d75a9-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d75a9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d75a9-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d75a9-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d75a9-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d75a9-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d75a9-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d75a9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d75a9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d75a9-119">See also</span></span>

- [<span data-ttu-id="d75a9-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d75a9-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
