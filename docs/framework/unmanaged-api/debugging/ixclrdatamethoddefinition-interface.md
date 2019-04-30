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
ms.openlocfilehash: 4b1e8cb1cf34bb1c5ade1353351aab953e2b734a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670111"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="7e1be-102">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e1be-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="7e1be-103">Bir yöntemin tanımı hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e1be-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="7e1be-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7e1be-104">Methods</span></span>

<span data-ttu-id="7e1be-105">Aşağıdaki yöntemlerden arabirimindeki yöntemleri bazılarıdır.</span><span class="sxs-lookup"><span data-stu-id="7e1be-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="7e1be-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7e1be-106">Method</span></span>                                                                                                                          | <span data-ttu-id="7e1be-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e1be-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="7e1be-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="7e1be-108">StartEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="7e1be-109">Numaralandırma yöntemi örnekleri için bir tanıtıcı sağlayan bir verilen `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="7e1be-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="7e1be-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="7e1be-110">EnumInstance</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="7e1be-111">Bu yöntem tanımını örneklerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="7e1be-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="7e1be-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="7e1be-112">EndEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="7e1be-113">Örnek numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="7e1be-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="7e1be-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e1be-114">Remarks</span></span>

<span data-ttu-id="7e1be-115">Bu arabirim, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="7e1be-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="7e1be-116">Ancak, bu, türetilen bir COM arabirimidir `IUnknown` GUID'e sahip `AAF60008-FB2C-420b-8FB1-42D244A54A97` normal COM mekanizmalar aracılığıyla edinilebilir.</span><span class="sxs-lookup"><span data-stu-id="7e1be-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e1be-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e1be-117">Requirements</span></span>

<span data-ttu-id="7e1be-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e1be-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7e1be-119">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="7e1be-119">**Header:** None</span></span>  
<span data-ttu-id="7e1be-120">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="7e1be-120">**Library:** None</span></span>  
<span data-ttu-id="7e1be-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7e1be-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7e1be-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e1be-122">See also</span></span>

- [<span data-ttu-id="7e1be-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7e1be-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7e1be-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7e1be-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
