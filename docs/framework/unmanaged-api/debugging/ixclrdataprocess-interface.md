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
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790369"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="ac73a-102">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac73a-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="ac73a-103">İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac73a-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ac73a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ac73a-104">Methods</span></span>

| <span data-ttu-id="ac73a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ac73a-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="ac73a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac73a-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ac73a-107">Getappdomainbyuniqueıd</span><span class="sxs-lookup"><span data-stu-id="ac73a-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="ac73a-108">Bir işlemdeki `AppDomain` benzersiz kimliğine göre alır.</span><span class="sxs-lookup"><span data-stu-id="ac73a-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="ac73a-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="ac73a-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="ac73a-110">Bir işlemin modüllerini numaralandırmak için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac73a-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="ac73a-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="ac73a-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="ac73a-112">Bu işlemin modüllerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ac73a-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="ac73a-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="ac73a-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="ac73a-114">Modül numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ac73a-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="ac73a-115">Startenummethodınstancesbyaddress</span><span class="sxs-lookup"><span data-stu-id="ac73a-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="ac73a-116">Verilen bir adresten başlayarak `AppDomain` metot örneklerini numaralandırmak için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac73a-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="ac73a-117">Enummethodınstancebyaddress</span><span class="sxs-lookup"><span data-stu-id="ac73a-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="ac73a-118">Bir adres uzaklığında başlayarak bu işlemin Yöntem örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ac73a-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="ac73a-119">Endenummethodınstancesbyaddress</span><span class="sxs-lookup"><span data-stu-id="ac73a-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="ac73a-120">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ac73a-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="ac73a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac73a-121">Remarks</span></span>

<span data-ttu-id="ac73a-122">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="ac73a-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ac73a-123">Ancak, normal COM mekanizmalarından elde edilebilir GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` `IUnknown` türetilen bir COM arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="ac73a-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac73a-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac73a-124">Requirements</span></span>

<span data-ttu-id="ac73a-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac73a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="ac73a-126">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="ac73a-126">**Header:** None</span></span>  
<span data-ttu-id="ac73a-127">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="ac73a-127">**Library:** None</span></span>  
<span data-ttu-id="ac73a-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ac73a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ac73a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac73a-129">See also</span></span>

- [<span data-ttu-id="ac73a-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ac73a-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="ac73a-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ac73a-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
