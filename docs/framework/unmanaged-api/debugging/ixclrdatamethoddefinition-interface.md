---
description: 'Daha fazla bilgi edinin: IXCLRDataMethodDefinition Interface'
title: IXCLRDataMethodDefinition Arabirimi
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d73246b42a0bfb982c87b04d5490e945f7caa745
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790353"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="93056-103">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93056-103">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="93056-104">Yöntem tanımı hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="93056-104">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="93056-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="93056-105">Methods</span></span>

<span data-ttu-id="93056-106">Aşağıdaki yöntemler, arabiriminde kullanılabilen yöntemlerin bazılarıdır.</span><span class="sxs-lookup"><span data-stu-id="93056-106">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="93056-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="93056-107">Method</span></span>                                                                                                                          | <span data-ttu-id="93056-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93056-108">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="93056-109">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="93056-109">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="93056-110">Belirli bir için yöntem örneklerinin numaralandırması için bir tanıtıcı sağlar `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="93056-110">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="93056-111">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="93056-111">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="93056-112">Bu yöntem tanımının örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="93056-112">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="93056-113">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="93056-113">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="93056-114">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="93056-114">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="93056-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93056-115">Remarks</span></span>

<span data-ttu-id="93056-116">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="93056-116">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="93056-117">Ancak, `IUnknown` `AAF60008-FB2C-420b-8FB1-42D244A54A97` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="93056-117">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="93056-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93056-118">Requirements</span></span>

<span data-ttu-id="93056-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93056-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="93056-120">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="93056-120">**Header:** None</span></span>  
<span data-ttu-id="93056-121">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="93056-121">**Library:** None</span></span>  
<span data-ttu-id="93056-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="93056-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="93056-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93056-123">See also</span></span>

- [<span data-ttu-id="93056-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="93056-124">Debugging</span></span>](index.md)
- [<span data-ttu-id="93056-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="93056-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
