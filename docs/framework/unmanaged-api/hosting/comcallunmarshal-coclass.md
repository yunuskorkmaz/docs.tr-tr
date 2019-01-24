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
ms.openlocfilehash: 5a404448c45a37d50794ceae9a9bf8ff6af08eeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574579"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="31d0e-102">ComCallUnmarshal Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="31d0e-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="31d0e-103">Arabirim işaretçilerini sıralama yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d0e-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31d0e-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="31d0e-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="31d0e-105">Interfaces</span></span>  
  
|<span data-ttu-id="31d0e-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="31d0e-106">Interface</span></span>|<span data-ttu-id="31d0e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31d0e-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="31d0e-108">Oluşturma, başlatma ve istemci işlemi proxy yönetme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d0e-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31d0e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31d0e-109">Requirements</span></span>  
 <span data-ttu-id="31d0e-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d0e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d0e-111">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="31d0e-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="31d0e-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="31d0e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31d0e-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d0e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d0e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31d0e-114">See also</span></span>
- [<span data-ttu-id="31d0e-115">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="31d0e-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
