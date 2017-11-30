---
title: ICLRProbingAssemblyEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum
helpviewer_keywords: ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6d810ab6e62c6df1b00305947de552ecdbe82141
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="9d132-102">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d132-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="9d132-103">Ortak dil çalışma zamanı (CLR) iç oluşturun veya kimliğe anlamak zorunda kalmadan derlemenin kimlik bilgilerini kullanarak bir derleme yoklama kimliklerini almak konak sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d132-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d132-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d132-104">Methods</span></span>  
  
|<span data-ttu-id="9d132-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9d132-105">Method</span></span>|<span data-ttu-id="9d132-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d132-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d132-107">Get yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d132-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="9d132-108">Belirtilen dizindeki derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="9d132-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d132-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d132-109">Remarks</span></span>  
 <span data-ttu-id="9d132-110">Gibi yöntemler [Iclrassemblyıdentitymanager::getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) dönüş bir `ICLRProbingAssemblyEnum` örneği.</span><span class="sxs-lookup"><span data-stu-id="9d132-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d132-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d132-111">Requirements</span></span>  
 <span data-ttu-id="9d132-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d132-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d132-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d132-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d132-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9d132-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d132-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d132-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d132-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d132-116">See Also</span></span>  
 [<span data-ttu-id="9d132-117">Iclrassemblyıdentitymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d132-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="9d132-118">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d132-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="9d132-119">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d132-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
