---
description: 'Daha fazla bilgi edinin: ComCallUnmarshal coclass'
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
ms.openlocfilehash: 508c1183e2862a286e9db0390bc0348629a9db8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799843"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="d71a5-103">ComCallUnmarshal Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="d71a5-103">ComCallUnmarshal Coclass</span></span>

<span data-ttu-id="d71a5-104">Arabirim işaretçilerinin sıralamasını yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d71a5-104">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71a5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d71a5-105">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="d71a5-106">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d71a5-106">Interfaces</span></span>  
  
|<span data-ttu-id="d71a5-107">Arabirim</span><span class="sxs-lookup"><span data-stu-id="d71a5-107">Interface</span></span>|<span data-ttu-id="d71a5-108">Description</span><span class="sxs-lookup"><span data-stu-id="d71a5-108">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="d71a5-109">İstemci işleminde bir proxy oluşturmak, başlatmak ve yönetmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d71a5-109">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d71a5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d71a5-110">Requirements</span></span>  

 <span data-ttu-id="d71a5-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d71a5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d71a5-112">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="d71a5-112">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d71a5-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d71a5-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d71a5-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d71a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71a5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d71a5-115">See also</span></span>

- [<span data-ttu-id="d71a5-116">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="d71a5-116">Hosting Coclasses</span></span>](hosting-coclasses.md)
