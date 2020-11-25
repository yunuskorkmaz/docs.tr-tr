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
ms.openlocfilehash: 90bcf4f37631e0246e58cc14bfcd331d981e4713
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731728"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="4e458-102">ComCallUnmarshal Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="4e458-102">ComCallUnmarshal Coclass</span></span>

<span data-ttu-id="4e458-103">Arabirim işaretçilerinin sıralamasını yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e458-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e458-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e458-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="4e458-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="4e458-105">Interfaces</span></span>  
  
|<span data-ttu-id="4e458-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="4e458-106">Interface</span></span>|<span data-ttu-id="4e458-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e458-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="4e458-108">İstemci işleminde bir proxy oluşturmak, başlatmak ve yönetmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e458-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e458-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e458-109">Requirements</span></span>  

 <span data-ttu-id="4e458-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e458-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e458-111">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="4e458-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4e458-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4e458-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e458-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e458-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e458-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e458-114">See also</span></span>

- [<span data-ttu-id="4e458-115">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="4e458-115">Hosting Coclasses</span></span>](hosting-coclasses.md)
