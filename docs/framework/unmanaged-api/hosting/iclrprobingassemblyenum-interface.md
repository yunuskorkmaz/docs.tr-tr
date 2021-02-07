---
description: ': ICLRProbingAssemblyEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1fd11e237f02bab85ec2b41df49d7d8a2f27e1e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716519"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="64994-103">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64994-103">ICLRProbingAssemblyEnum Interface</span></span>

<span data-ttu-id="64994-104">Ana bilgisayarın, ortak dil çalışma zamanına (CLR) ait kimlik bilgilerini kullanarak, bu kimliği oluşturmak veya anlamak zorunda kalmadan bir derlemenin yoklama kimliklerini almasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="64994-104">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64994-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="64994-105">Methods</span></span>  
  
|<span data-ttu-id="64994-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="64994-106">Method</span></span>|<span data-ttu-id="64994-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64994-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64994-108">Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64994-108">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="64994-109">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="64994-109">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64994-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64994-110">Remarks</span></span>  

 <span data-ttu-id="64994-111">[ICLRAssemblyIdentityManager:: Getprobing, Liesfromreference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) gibi yöntemler bir örnek döndürür `ICLRProbingAssemblyEnum` .</span><span class="sxs-lookup"><span data-stu-id="64994-111">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64994-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64994-112">Requirements</span></span>  

 <span data-ttu-id="64994-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64994-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64994-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="64994-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64994-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="64994-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64994-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64994-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64994-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64994-117">See also</span></span>

- [<span data-ttu-id="64994-118">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64994-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="64994-119">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64994-119">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="64994-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64994-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
