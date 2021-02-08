---
description: 'Şu konuda daha fazla bilgi edinin: IApartmentCallback arabirimi'
title: IApartmentCallback Arabirimi
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
ms.openlocfilehash: ddf99b1d926bd2d9765b936143785a975ea378a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785148"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="aff08-103">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aff08-103">IApartmentCallback Interface</span></span>

<span data-ttu-id="aff08-104">Bir grup içinde geri çağırma yapmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aff08-104">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="aff08-105">*Apartman* , aynı iş parçacığı erişim gereksinimlerini paylaşan nesneler için bir işlem içindeki mantıksal bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="aff08-105">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aff08-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aff08-106">Methods</span></span>  
  
|<span data-ttu-id="aff08-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aff08-107">Method</span></span>|<span data-ttu-id="aff08-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff08-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aff08-109">DoCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aff08-109">DoCallback Method</span></span>](iapartmentcallback-docallback-method.md)|<span data-ttu-id="aff08-110">Belirtilen işlevi bir apartman içinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="aff08-110">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aff08-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aff08-111">Requirements</span></span>  

 <span data-ttu-id="aff08-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff08-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aff08-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aff08-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aff08-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="aff08-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aff08-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aff08-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff08-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aff08-116">See also</span></span>

- [<span data-ttu-id="aff08-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aff08-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
