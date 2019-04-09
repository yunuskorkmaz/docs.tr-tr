---
title: ICLRProbingAssemblyEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 118345f246de3d7ee68d51cf37e8cdea9de1fdba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094300"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="9e18b-102">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e18b-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="9e18b-103">Oluşturma veya kimliğe anlamanıza gerek kalmadan iç ortak dil çalışma zamanı (CLR), derlemenin kimlik bilgilerini kullanarak bir derleme araştırma kimliklerini almak konağı etkinleştirme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e18b-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e18b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e18b-104">Methods</span></span>  
  
|<span data-ttu-id="9e18b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9e18b-105">Method</span></span>|<span data-ttu-id="9e18b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e18b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e18b-107">Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e18b-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="9e18b-108">Belirtilen dizindeki derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="9e18b-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e18b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e18b-109">Remarks</span></span>  
 <span data-ttu-id="9e18b-110">Yöntemler gibi [Iclrassemblyıdentitymanager::getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) dönüş bir `ICLRProbingAssemblyEnum` örneği.</span><span class="sxs-lookup"><span data-stu-id="9e18b-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e18b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e18b-111">Requirements</span></span>  
 <span data-ttu-id="9e18b-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e18b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e18b-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e18b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e18b-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9e18b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9e18b-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9e18b-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e18b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e18b-116">See also</span></span>

- [<span data-ttu-id="9e18b-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e18b-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="9e18b-118">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e18b-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9e18b-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e18b-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
