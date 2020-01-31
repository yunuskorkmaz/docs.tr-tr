---
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
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790421"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="137de-102">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="137de-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="137de-103">Yöntem tanımı hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="137de-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="137de-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="137de-104">Methods</span></span>

<span data-ttu-id="137de-105">Aşağıdaki yöntemler, arabiriminde kullanılabilen yöntemlerin bazılarıdır.</span><span class="sxs-lookup"><span data-stu-id="137de-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="137de-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="137de-106">Method</span></span>                                                                                                                          | <span data-ttu-id="137de-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="137de-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="137de-108">Startenumınstances</span><span class="sxs-lookup"><span data-stu-id="137de-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="137de-109">Belirli bir `IXCLRDataAppDomain`için yöntem örneklerinin numaralandırılması için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="137de-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="137de-110">Enumınstance</span><span class="sxs-lookup"><span data-stu-id="137de-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="137de-111">Bu yöntem tanımının örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="137de-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="137de-112">Endenumınstances</span><span class="sxs-lookup"><span data-stu-id="137de-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="137de-113">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="137de-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="137de-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="137de-114">Remarks</span></span>

<span data-ttu-id="137de-115">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="137de-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="137de-116">Ancak, normal COM mekanizmalarından elde edilebilir GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` `IUnknown` türetilen bir COM arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="137de-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="137de-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="137de-117">Requirements</span></span>

<span data-ttu-id="137de-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="137de-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="137de-119">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="137de-119">**Header:** None</span></span>  
<span data-ttu-id="137de-120">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="137de-120">**Library:** None</span></span>  
<span data-ttu-id="137de-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="137de-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="137de-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="137de-122">See also</span></span>

- [<span data-ttu-id="137de-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="137de-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="137de-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="137de-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
