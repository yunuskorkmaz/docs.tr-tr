---
title: ICLRReferenceAssemblyEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRReferenceAssemblyEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRReferenceAssemblyEnum
helpviewer_keywords: ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d2a295c4c35761d0a47e1690cd7b88387cecdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="7a42e-102">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a42e-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="7a42e-103">Bir dosya veya ortak dil çalışma zamanı (CLR) iç oluşturun veya bu kimlikleri anlamak zorunda kalmadan derleme kimlik verilerini kullanarak akış tarafından başvurulan derlemeler kümesini işlemek için ana izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a42e-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a42e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7a42e-104">Methods</span></span>  
  
|<span data-ttu-id="7a42e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7a42e-105">Method</span></span>|<span data-ttu-id="7a42e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a42e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a42e-107">Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a42e-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="7a42e-108">Sağlanan dizininde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="7a42e-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a42e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a42e-109">Requirements</span></span>  
 <span data-ttu-id="7a42e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a42e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a42e-111">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7a42e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a42e-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7a42e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a42e-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a42e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a42e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a42e-114">See Also</span></span>  
 [<span data-ttu-id="7a42e-115">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a42e-115">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="7a42e-116">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a42e-116">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="7a42e-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7a42e-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
