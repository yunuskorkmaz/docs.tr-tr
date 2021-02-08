---
description: 'Daha fazla bilgi edinin: IXCLRDataProcess Interface'
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
ms.openlocfilehash: b611491e5c9a5957c07a305a3f395b67ad208649
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800649"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="4a1e7-103">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a1e7-103">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="4a1e7-104">İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-104">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="4a1e7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4a1e7-105">Methods</span></span>

| <span data-ttu-id="4a1e7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4a1e7-106">Method</span></span>                                                                                                                                               | <span data-ttu-id="4a1e7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a1e7-107">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="4a1e7-108">GetRuntimeNameByAddress</span><span class="sxs-lookup"><span data-stu-id="4a1e7-108">GetRuntimeNameByAddress</span></span>](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | <span data-ttu-id="4a1e7-109">Verilen adres için bir ad alır.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-109">Gets a name for the given address.</span></span>                                                               |
| [<span data-ttu-id="4a1e7-110">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="4a1e7-110">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="4a1e7-111">Bir `AppDomain` işlem içinde kendi benzersiz kimliğine göre alır.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-111">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="4a1e7-112">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="4a1e7-112">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="4a1e7-113">Bir işlemin modüllerini numaralandırmak için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-113">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="4a1e7-114">EnumModule</span><span class="sxs-lookup"><span data-stu-id="4a1e7-114">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="4a1e7-115">Bu işlemin modüllerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-115">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="4a1e7-116">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="4a1e7-116">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="4a1e7-117">Modül numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-117">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="4a1e7-118">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="4a1e7-118">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="4a1e7-119">Verilen bir adresten başlayarak Yöntem örneklerinin numaralandırılacağı bir tanıtıcı sağlar `AppDomain` .</span><span class="sxs-lookup"><span data-stu-id="4a1e7-119">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="4a1e7-120">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="4a1e7-120">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="4a1e7-121">Bir adres uzaklığında başlayarak bu işlemin Yöntem örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-121">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="4a1e7-122">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="4a1e7-122">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="4a1e7-123">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-123">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="4a1e7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a1e7-124">Remarks</span></span>

<span data-ttu-id="4a1e7-125">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-125">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="4a1e7-126">Ancak, `IUnknown` `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-126">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a1e7-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a1e7-127">Requirements</span></span>

<span data-ttu-id="4a1e7-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a1e7-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="4a1e7-129">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="4a1e7-129">**Header:** None</span></span>  
<span data-ttu-id="4a1e7-130">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="4a1e7-130">**Library:** None</span></span>  
<span data-ttu-id="4a1e7-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4a1e7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4a1e7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a1e7-132">See also</span></span>

- [<span data-ttu-id="4a1e7-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4a1e7-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="4a1e7-134">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a1e7-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
