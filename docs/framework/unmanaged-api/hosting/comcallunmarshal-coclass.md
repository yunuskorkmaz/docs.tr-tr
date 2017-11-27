---
title: "ComCallUnmarshal Coclass’ı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ComCallUnmarshal Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: ComCallUnmarshal
helpviewer_keywords: ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2760fc84466c85e022421bcc17dcee6444ec859a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="59394-102">ComCallUnmarshal Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="59394-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="59394-103">Arabirim İşaretçileri hazırlama yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="59394-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59394-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59394-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="59394-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="59394-105">Interfaces</span></span>  
  
|<span data-ttu-id="59394-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="59394-106">Interface</span></span>|<span data-ttu-id="59394-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59394-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="59394-108">Oluşturma, başlatma ve bir istemci işlemi proxy yönetme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="59394-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59394-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59394-109">Requirements</span></span>  
 <span data-ttu-id="59394-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59394-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59394-111">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="59394-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="59394-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="59394-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59394-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59394-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59394-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59394-114">See Also</span></span>  
 [<span data-ttu-id="59394-115">Barındırma coclass'ları</span><span class="sxs-lookup"><span data-stu-id="59394-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
