---
description: 'Şu konuda daha fazla bilgi edinin: ICLRAssemblyIdentityManager arabirimi'
title: ICLRAssemblyIdentityManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: d6238ec51a8cc1bb61eaa96e5297656c447df785
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790065"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="cbd1a-103">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-103">ICLRAssemblyIdentityManager Interface</span></span>

<span data-ttu-id="cbd1a-104">Derlemeler hakkında, ana bilgisayar ve ortak dil çalışma zamanı (CLR) arasındaki iletişimi destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-104">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cbd1a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cbd1a-105">Methods</span></span>  
  
|<span data-ttu-id="cbd1a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cbd1a-106">Method</span></span>|<span data-ttu-id="cbd1a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbd1a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cbd1a-108">GetBindingIdentityFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-108">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="cbd1a-109">Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-109">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="cbd1a-110">GetBindingIdentityFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-110">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="cbd1a-111">Belirtilen akıştaki derleme için kurallı derleme kimliği verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-111">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="cbd1a-112">GetCLRAssemblyReferenceList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-112">GetCLRAssemblyReferenceList Method</span></span>](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="cbd1a-113">Sağlanan kısmi derleme kimlikleri listesinden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) örneği alır.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-113">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="cbd1a-114">GetProbingAssembliesFromReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-114">GetProbingAssembliesFromReference Method</span></span>](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="cbd1a-115">Belirtilen kimliğe sahip derleme tarafından başvurulan derleme kimlikleri için bir [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) numaralandırıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-115">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="cbd1a-116">GetReferencedAssembliesFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-116">GetReferencedAssembliesFromFile Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="cbd1a-117">Belirtilen dosya yolundaki derleme tarafından başvurulan derlemelerin listesini içeren bir [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-117">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="cbd1a-118">GetReferencedAssembliesFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-118">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="cbd1a-119">`ICLRReferenceAssemblyEnum`Belirtilen akıştaki derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren bir nesneye yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-119">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="cbd1a-120">IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-120">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="cbd1a-121">Belirtilen derlemenin kesin olarak adlandırılmış olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-121">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbd1a-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbd1a-122">Remarks</span></span>  

 <span data-ttu-id="cbd1a-123">`ICLRAssemblyIdentityManager` `ICLRAssemblyReferenceList` Derleme kimliklerini listelemek ve örnekleri almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-123">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbd1a-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbd1a-124">Requirements</span></span>  

 <span data-ttu-id="cbd1a-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd1a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd1a-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cbd1a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbd1a-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbd1a-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd1a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd1a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbd1a-129">See also</span></span>

- [<span data-ttu-id="cbd1a-130">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-130">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="cbd1a-131">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbd1a-131">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="cbd1a-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cbd1a-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
