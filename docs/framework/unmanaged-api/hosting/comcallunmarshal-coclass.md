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
ms.openlocfilehash: 38f3140a181deae1a86569bfc2eb7cf3cd7d1991
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131924"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="1699f-102">ComCallUnmarshal Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="1699f-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="1699f-103">Arabirim işaretçilerinin sıralamasını yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1699f-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1699f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1699f-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="1699f-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="1699f-105">Interfaces</span></span>  
  
|<span data-ttu-id="1699f-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="1699f-106">Interface</span></span>|<span data-ttu-id="1699f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1699f-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="1699f-108">İstemci işleminde bir proxy oluşturmak, başlatmak ve yönetmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1699f-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1699f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1699f-109">Requirements</span></span>  
 <span data-ttu-id="1699f-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1699f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1699f-111">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="1699f-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="1699f-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1699f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1699f-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1699f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1699f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1699f-114">See also</span></span>

- [<span data-ttu-id="1699f-115">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="1699f-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
