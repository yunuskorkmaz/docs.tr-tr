---
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
ms.openlocfilehash: 3611de471001d31c40984e71d49ce376bb3e4607
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504296"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="aeaa3-102">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="aeaa3-103">Derlemeler hakkında, ana bilgisayar ve ortak dil çalışma zamanı (CLR) arasındaki iletişimi destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aeaa3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aeaa3-104">Methods</span></span>  
  
|<span data-ttu-id="aeaa3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aeaa3-105">Method</span></span>|<span data-ttu-id="aeaa3-106">Description</span><span class="sxs-lookup"><span data-stu-id="aeaa3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aeaa3-107">GetBindingIdentityFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-107">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="aeaa3-108">Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="aeaa3-109">GetBindingIdentityFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-109">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="aeaa3-110">Belirtilen akıştaki derleme için kurallı derleme kimliği verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="aeaa3-111">GetCLRAssemblyReferenceList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-111">GetCLRAssemblyReferenceList Method</span></span>](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="aeaa3-112">Sağlanan kısmi derleme kimlikleri listesinden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) örneği alır.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-112">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="aeaa3-113">GetProbingAssembliesFromReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-113">GetProbingAssembliesFromReference Method</span></span>](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="aeaa3-114">Belirtilen kimliğe sahip derleme tarafından başvurulan derleme kimlikleri için bir [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) numaralandırıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-114">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="aeaa3-115">GetReferencedAssembliesFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-115">GetReferencedAssembliesFromFile Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="aeaa3-116">Belirtilen dosya yolundaki derleme tarafından başvurulan derlemelerin listesini içeren bir [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-116">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="aeaa3-117">GetReferencedAssembliesFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-117">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="aeaa3-118">`ICLRReferenceAssemblyEnum`Belirtilen akıştaki derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren bir nesneye yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="aeaa3-119">IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-119">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="aeaa3-120">Belirtilen derlemenin kesin olarak adlandırılmış olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeaa3-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeaa3-121">Remarks</span></span>  
 <span data-ttu-id="aeaa3-122">`ICLRAssemblyIdentityManager` `ICLRAssemblyReferenceList` Derleme kimliklerini listelemek ve örnekleri almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeaa3-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeaa3-123">Requirements</span></span>  
 <span data-ttu-id="aeaa3-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeaa3-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeaa3-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aeaa3-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeaa3-126">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="aeaa3-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeaa3-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeaa3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeaa3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeaa3-128">See also</span></span>

- [<span data-ttu-id="aeaa3-129">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-129">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="aeaa3-130">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeaa3-130">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="aeaa3-131">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aeaa3-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
