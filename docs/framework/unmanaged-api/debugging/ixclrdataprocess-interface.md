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
ms.openlocfilehash: 6a6def8fc10f04b89aa8d8c735025b01f9b6ddfb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420766"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="32f29-102">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32f29-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="32f29-103">İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="32f29-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="32f29-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="32f29-104">Methods</span></span>

| <span data-ttu-id="32f29-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="32f29-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="32f29-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32f29-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="32f29-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="32f29-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="32f29-108">Bir `AppDomain` işlem içinde kendi benzersiz kimliğine göre alır.</span><span class="sxs-lookup"><span data-stu-id="32f29-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="32f29-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="32f29-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="32f29-110">Bir işlemin modüllerini numaralandırmak için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="32f29-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="32f29-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="32f29-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="32f29-112">Bu işlemin modüllerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="32f29-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="32f29-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="32f29-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="32f29-114">Modül numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="32f29-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="32f29-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="32f29-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="32f29-116">Verilen bir adresten başlayarak Yöntem örneklerinin numaralandırılacağı bir tanıtıcı sağlar `AppDomain` .</span><span class="sxs-lookup"><span data-stu-id="32f29-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="32f29-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="32f29-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="32f29-118">Bir adres uzaklığında başlayarak bu işlemin Yöntem örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="32f29-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="32f29-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="32f29-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="32f29-120">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="32f29-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="32f29-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32f29-121">Remarks</span></span>

<span data-ttu-id="32f29-122">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="32f29-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="32f29-123">Ancak, `IUnknown` `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="32f29-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="32f29-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32f29-124">Requirements</span></span>

<span data-ttu-id="32f29-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32f29-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="32f29-126">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="32f29-126">**Header:** None</span></span>  
<span data-ttu-id="32f29-127">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="32f29-127">**Library:** None</span></span>  
<span data-ttu-id="32f29-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32f29-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="32f29-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32f29-129">See also</span></span>

- [<span data-ttu-id="32f29-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="32f29-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="32f29-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="32f29-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
