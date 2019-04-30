---
title: IXCLRDataProcess Arabirimi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ff74a7acb5cc84c177f083c19402cd78977aeab5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775251"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="ee59b-102">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee59b-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="ee59b-103">Bir işlem hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee59b-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ee59b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ee59b-104">Methods</span></span>

| <span data-ttu-id="ee59b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ee59b-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="ee59b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee59b-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ee59b-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="ee59b-107">GetAppDomainByUniqueId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="ee59b-108">Alır bir `AppDomain` benzersiz kimliğine göre bir işlemde.</span><span class="sxs-lookup"><span data-stu-id="ee59b-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="ee59b-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="ee59b-109">StartEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="ee59b-110">Bir işlemin modülleri listelemek için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee59b-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="ee59b-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="ee59b-111">EnumModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="ee59b-112">Bu işlemin modülleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ee59b-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="ee59b-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="ee59b-113">EndEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="ee59b-114">Modül numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ee59b-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="ee59b-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="ee59b-115">StartEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="ee59b-116">Yöntem örneklerini listelemek için bir tanıtıcı sağlar `AppDomain` belirli bir adreste başlayan.</span><span class="sxs-lookup"><span data-stu-id="ee59b-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="ee59b-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="ee59b-117">EnumMethodInstanceByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="ee59b-118">Bu işlem bir adresi uzaklıkta başlayan yöntemi örneklerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="ee59b-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="ee59b-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="ee59b-119">EndEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="ee59b-120">Örnek numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ee59b-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="ee59b-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee59b-121">Remarks</span></span>

<span data-ttu-id="ee59b-122">Bu arabirim, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="ee59b-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ee59b-123">Ancak, bu, türetilen bir COM arabirimidir `IUnknown` GUID'e sahip `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` normal COM mekanizmalar aracılığıyla edinilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee59b-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee59b-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee59b-124">Requirements</span></span>

<span data-ttu-id="ee59b-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee59b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="ee59b-126">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="ee59b-126">**Header:** None</span></span>  
<span data-ttu-id="ee59b-127">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="ee59b-127">**Library:** None</span></span>  
<span data-ttu-id="ee59b-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ee59b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ee59b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee59b-129">See also</span></span>

- [<span data-ttu-id="ee59b-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ee59b-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ee59b-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ee59b-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
