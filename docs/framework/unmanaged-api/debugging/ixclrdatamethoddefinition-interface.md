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
ms.openlocfilehash: ebb689eee4a89a70e81d8f9d958e7826c3b3421b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420961"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="d48d8-102">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d48d8-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="d48d8-103">Yöntem tanımı hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d48d8-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="d48d8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d48d8-104">Methods</span></span>

<span data-ttu-id="d48d8-105">Aşağıdaki yöntemler, arabiriminde kullanılabilen yöntemlerin bazılarıdır.</span><span class="sxs-lookup"><span data-stu-id="d48d8-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="d48d8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d48d8-106">Method</span></span>                                                                                                                          | <span data-ttu-id="d48d8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d48d8-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="d48d8-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="d48d8-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="d48d8-109">Belirli bir için yöntem örneklerinin numaralandırması için bir tanıtıcı sağlar `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="d48d8-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="d48d8-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="d48d8-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="d48d8-111">Bu yöntem tanımının örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d48d8-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="d48d8-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="d48d8-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="d48d8-113">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="d48d8-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="d48d8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d48d8-114">Remarks</span></span>

<span data-ttu-id="d48d8-115">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="d48d8-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="d48d8-116">Ancak, `IUnknown` `AAF60008-FB2C-420b-8FB1-42D244A54A97` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="d48d8-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="d48d8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d48d8-117">Requirements</span></span>

<span data-ttu-id="d48d8-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d48d8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d48d8-119">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="d48d8-119">**Header:** None</span></span>  
<span data-ttu-id="d48d8-120">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="d48d8-120">**Library:** None</span></span>  
<span data-ttu-id="d48d8-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d48d8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d48d8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d48d8-122">See also</span></span>

- [<span data-ttu-id="d48d8-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d48d8-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="d48d8-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d48d8-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
