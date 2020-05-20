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
ms.openlocfilehash: e1e114070f39e75254fc1bc0f8c1bf3e4733d5a2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703377"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="4d1b3-102">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d1b3-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="4d1b3-103">Ana bilgisayarın, ortak dil çalışma zamanına (CLR) ait kimlik bilgilerini kullanarak, bu kimliği oluşturmak veya anlamak zorunda kalmadan bir derlemenin yoklama kimliklerini almasını sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d1b3-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d1b3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4d1b3-104">Methods</span></span>  
  
|<span data-ttu-id="4d1b3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4d1b3-105">Method</span></span>|<span data-ttu-id="4d1b3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d1b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d1b3-107">Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d1b3-107">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="4d1b3-108">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="4d1b3-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d1b3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d1b3-109">Remarks</span></span>  
 <span data-ttu-id="4d1b3-110">[ICLRAssemblyIdentityManager:: Getprobing, Liesfromreference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) gibi yöntemler bir örnek döndürür `ICLRProbingAssemblyEnum` .</span><span class="sxs-lookup"><span data-stu-id="4d1b3-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d1b3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d1b3-111">Requirements</span></span>  
 <span data-ttu-id="4d1b3-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d1b3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d1b3-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d1b3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d1b3-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4d1b3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d1b3-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d1b3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1b3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d1b3-116">See also</span></span>

- [<span data-ttu-id="4d1b3-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d1b3-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="4d1b3-118">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d1b3-118">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4d1b3-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4d1b3-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
