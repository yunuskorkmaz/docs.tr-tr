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
ms.openlocfilehash: 2f17a88a90905006432ae8c5dc040277124c947b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166887"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="c3dc6-102">ComCallUnmarshal Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="c3dc6-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="c3dc6-103">Arabirim işaretçilerini sıralama yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3dc6-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3dc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3dc6-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="c3dc6-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="c3dc6-105">Interfaces</span></span>  
  
|<span data-ttu-id="c3dc6-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="c3dc6-106">Interface</span></span>|<span data-ttu-id="c3dc6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3dc6-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="c3dc6-108">Oluşturma, başlatma ve istemci işlemi proxy yönetme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3dc6-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3dc6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3dc6-109">Requirements</span></span>  
 <span data-ttu-id="c3dc6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3dc6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3dc6-111">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="c3dc6-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c3dc6-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c3dc6-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c3dc6-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c3dc6-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3dc6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3dc6-114">See also</span></span>

- [<span data-ttu-id="c3dc6-115">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="c3dc6-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
