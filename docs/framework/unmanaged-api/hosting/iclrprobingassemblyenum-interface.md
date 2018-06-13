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
ms.openlocfilehash: c295a5633dedf1f0c85a9a697fea5524ee03fafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432704"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="1d54b-102">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d54b-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="1d54b-103">Ortak dil çalışma zamanı (CLR) iç oluşturun veya kimliğe anlamak zorunda kalmadan derlemenin kimlik bilgilerini kullanarak bir derleme yoklama kimliklerini almak konak sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d54b-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d54b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d54b-104">Methods</span></span>  
  
|<span data-ttu-id="1d54b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1d54b-105">Method</span></span>|<span data-ttu-id="1d54b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d54b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d54b-107">Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d54b-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="1d54b-108">Belirtilen dizindeki derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="1d54b-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d54b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d54b-109">Remarks</span></span>  
 <span data-ttu-id="1d54b-110">Gibi yöntemler [Iclrassemblyıdentitymanager::getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) dönüş bir `ICLRProbingAssemblyEnum` örneği.</span><span class="sxs-lookup"><span data-stu-id="1d54b-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d54b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d54b-111">Requirements</span></span>  
 <span data-ttu-id="1d54b-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d54b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d54b-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d54b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d54b-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1d54b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d54b-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d54b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d54b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d54b-116">See Also</span></span>  
 [<span data-ttu-id="1d54b-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d54b-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="1d54b-118">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d54b-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="1d54b-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1d54b-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
