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
ms.openlocfilehash: 939acc0ad47021d5fdffe7b7b71ea6a4a1635a6d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616742"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="3d05b-102">ComCallUnmarshal Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="3d05b-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="3d05b-103">Arabirim işaretçilerinin sıralamasını yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d05b-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d05b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3d05b-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="3d05b-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="3d05b-105">Interfaces</span></span>  
  
|<span data-ttu-id="3d05b-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="3d05b-106">Interface</span></span>|<span data-ttu-id="3d05b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d05b-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="3d05b-108">İstemci işleminde bir proxy oluşturmak, başlatmak ve yönetmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d05b-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d05b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d05b-109">Requirements</span></span>  
 <span data-ttu-id="3d05b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d05b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d05b-111">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="3d05b-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="3d05b-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3d05b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d05b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d05b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d05b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d05b-114">See also</span></span>

- [<span data-ttu-id="3d05b-115">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="3d05b-115">Hosting Coclasses</span></span>](hosting-coclasses.md)
