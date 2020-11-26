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
ms.openlocfilehash: 376ec2b840bc17c79ed1f27c17a8ddd22c37a0f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245360"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="794df-102">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="794df-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="794df-103">İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="794df-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="794df-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="794df-104">Methods</span></span>

| <span data-ttu-id="794df-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="794df-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="794df-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="794df-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="794df-107">GetRuntimeNameByAddress</span><span class="sxs-lookup"><span data-stu-id="794df-107">GetRuntimeNameByAddress</span></span>](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | <span data-ttu-id="794df-108">Verilen adres için bir ad alır.</span><span class="sxs-lookup"><span data-stu-id="794df-108">Gets a name for the given address.</span></span>                                                               |
| [<span data-ttu-id="794df-109">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="794df-109">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="794df-110">Bir `AppDomain` işlem içinde kendi benzersiz kimliğine göre alır.</span><span class="sxs-lookup"><span data-stu-id="794df-110">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="794df-111">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="794df-111">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="794df-112">Bir işlemin modüllerini numaralandırmak için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="794df-112">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="794df-113">EnumModule</span><span class="sxs-lookup"><span data-stu-id="794df-113">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="794df-114">Bu işlemin modüllerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="794df-114">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="794df-115">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="794df-115">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="794df-116">Modül numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="794df-116">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="794df-117">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="794df-117">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="794df-118">Verilen bir adresten başlayarak Yöntem örneklerinin numaralandırılacağı bir tanıtıcı sağlar `AppDomain` .</span><span class="sxs-lookup"><span data-stu-id="794df-118">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="794df-119">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="794df-119">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="794df-120">Bir adres uzaklığında başlayarak bu işlemin Yöntem örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="794df-120">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="794df-121">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="794df-121">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="794df-122">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="794df-122">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="794df-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="794df-123">Remarks</span></span>

<span data-ttu-id="794df-124">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="794df-124">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="794df-125">Ancak, `IUnknown` `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="794df-125">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="794df-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="794df-126">Requirements</span></span>

<span data-ttu-id="794df-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="794df-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="794df-128">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="794df-128">**Header:** None</span></span>  
<span data-ttu-id="794df-129">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="794df-129">**Library:** None</span></span>  
<span data-ttu-id="794df-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="794df-130">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="794df-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="794df-131">See also</span></span>

- [<span data-ttu-id="794df-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="794df-132">Debugging</span></span>](index.md)
- [<span data-ttu-id="794df-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="794df-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
