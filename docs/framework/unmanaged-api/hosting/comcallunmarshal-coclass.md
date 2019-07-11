---
title: ComCallUnmarshal Coclass’ı
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fde42e3ecfac81a168920bc152833be7ba72b995
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779087"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="52f73-102">ComCallUnmarshal Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="52f73-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="52f73-103">Arabirim işaretçilerini sıralama yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="52f73-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f73-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52f73-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="52f73-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="52f73-105">Interfaces</span></span>  
  
|<span data-ttu-id="52f73-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="52f73-106">Interface</span></span>|<span data-ttu-id="52f73-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52f73-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="52f73-108">Oluşturma, başlatma ve istemci işlemi proxy yönetme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="52f73-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52f73-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52f73-109">Requirements</span></span>  
 <span data-ttu-id="52f73-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52f73-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f73-111">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="52f73-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="52f73-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="52f73-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52f73-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f73-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f73-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52f73-114">See also</span></span>

- [<span data-ttu-id="52f73-115">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="52f73-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
