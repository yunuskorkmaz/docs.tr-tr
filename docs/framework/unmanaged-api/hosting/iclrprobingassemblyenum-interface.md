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
ms.openlocfilehash: e1459c1604f3f8f043fd9b61533235ab7861c910
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120556"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="90cd5-102">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90cd5-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="90cd5-103">Ana bilgisayarın, ortak dil çalışma zamanına (CLR) ait kimlik bilgilerini kullanarak, bu kimliği oluşturmak veya anlamak zorunda kalmadan bir derlemenin yoklama kimliklerini almasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="90cd5-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90cd5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="90cd5-104">Methods</span></span>  
  
|<span data-ttu-id="90cd5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="90cd5-105">Method</span></span>|<span data-ttu-id="90cd5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90cd5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90cd5-107">Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90cd5-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="90cd5-108">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="90cd5-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90cd5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90cd5-109">Remarks</span></span>  
 <span data-ttu-id="90cd5-110">[ICLRAssemblyIdentityManager:: Getprobing, Liesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) gibi yöntemler bir `ICLRProbingAssemblyEnum` örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="90cd5-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90cd5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90cd5-111">Requirements</span></span>  
 <span data-ttu-id="90cd5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90cd5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90cd5-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="90cd5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90cd5-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="90cd5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90cd5-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90cd5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90cd5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90cd5-116">See also</span></span>

- [<span data-ttu-id="90cd5-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90cd5-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="90cd5-118">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90cd5-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="90cd5-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="90cd5-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
