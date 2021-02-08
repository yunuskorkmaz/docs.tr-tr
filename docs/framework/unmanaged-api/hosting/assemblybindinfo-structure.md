---
description: 'Daha fazla bilgi edinin: AssemblyBindInfo yapısı'
title: AssemblyBindInfo Yapısı
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 3e11e05924ee6818737f84d9ca92394ee5313292
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799986"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="1dcc4-103">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="1dcc4-103">AssemblyBindInfo Structure</span></span>

<span data-ttu-id="1dcc4-104">Başvurulan derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-104">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dcc4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1dcc4-105">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="1dcc4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1dcc4-106">Members</span></span>  
  
|<span data-ttu-id="1dcc4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="1dcc4-107">Member</span></span>|<span data-ttu-id="1dcc4-108">Description</span><span class="sxs-lookup"><span data-stu-id="1dcc4-108">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="1dcc4-109">`IStream` [IHostAssemblyStore](ihostassemblystore-provideassembly-method.md)çağrısı tarafından döndürülen benzersiz bir tanımlayıcı::P rovideassembly, başvurulan derlemenin yükleneceği.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-109">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="1dcc4-110">Başvurulan derleme için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-110">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="1dcc4-111">Bağlama ilkesi değerlerinin uygulamadan sonra başvurulan derlemenin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-111">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="1dcc4-112">Varsa, başvurulan derlemeye hangi sürüm oluşturma ilkelerinin uygulanacağını belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-112">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dcc4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dcc4-113">Remarks</span></span>  

 <span data-ttu-id="1dcc4-114">Ana bilgisayar, `dwAppDomainId` ortak dil çalışma zamanına (CLR) benzersiz tanımlayıcıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-114">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="1dcc4-115">Bir çağrıdan sonra `IHostAssemblyStore::ProvideAssembly` , çalışma zamanı, ' ın içeriklerinin eşlenip eşlenmediğini anlamak için tanımlayıcıyı kullanır `IStream` .</span><span class="sxs-lookup"><span data-stu-id="1dcc4-115">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="1dcc4-116">Öyleyse, çalışma zamanı akışı yeniden eşleme yerine mevcut kopyayı yükler.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-116">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="1dcc4-117">Çalışma zamanı Ayrıca bu tanımlayıcıyı [IHostAssemblyStore](ihostassemblystore-providemodule-method.md)çağrılarından döndürülen akışlar için bir arama anahtarı olarak kullanır::P rovideModule.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-117">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="1dcc4-118">Bu nedenle, tanımlayıcı modül istekleri ve derleme istekleri için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-118">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dcc4-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dcc4-119">Requirements</span></span>  

 <span data-ttu-id="1dcc4-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dcc4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dcc4-121">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="1dcc4-121">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="1dcc4-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1dcc4-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dcc4-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dcc4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dcc4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dcc4-124">See also</span></span>

- [<span data-ttu-id="1dcc4-125">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="1dcc4-125">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="1dcc4-126">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dcc4-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="1dcc4-127">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dcc4-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1dcc4-128">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dcc4-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="1dcc4-129">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dcc4-129">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="1dcc4-130">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="1dcc4-130">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
