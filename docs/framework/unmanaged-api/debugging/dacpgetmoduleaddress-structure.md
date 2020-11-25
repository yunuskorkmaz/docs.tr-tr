---
title: DacpGetModuleAddress Yapısı
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a65fa9974165fa36e59a7fb83dca6dd902f7d8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724401"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="3074b-102">DacpGetModuleAddress Yapısı</span><span class="sxs-lookup"><span data-stu-id="3074b-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="3074b-103">Modül adresi isteği için kapsayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3074b-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3074b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3074b-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="3074b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3074b-105">Members</span></span>

| <span data-ttu-id="3074b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3074b-106">Member</span></span>      | <span data-ttu-id="3074b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3074b-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="3074b-108">Modülün işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3074b-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="3074b-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3074b-109">Methods</span></span>

| <span data-ttu-id="3074b-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3074b-110">Method</span></span>                                                                                               | <span data-ttu-id="3074b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3074b-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="3074b-112">İstek</span><span class="sxs-lookup"><span data-stu-id="3074b-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="3074b-113">Yapıyı verilen çalışma zamanı yapısından doldurma isteği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3074b-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3074b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3074b-114">Remarks</span></span>

<span data-ttu-id="3074b-115">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="3074b-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3074b-116">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın; burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="3074b-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="3074b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3074b-117">Requirements</span></span>

<span data-ttu-id="3074b-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3074b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3074b-119">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="3074b-119">**Header:** None</span></span>  
<span data-ttu-id="3074b-120">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="3074b-120">**Library:** None</span></span>  
<span data-ttu-id="3074b-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3074b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3074b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3074b-122">See also</span></span>

- [<span data-ttu-id="3074b-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3074b-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="3074b-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="3074b-124">Debugging Structures</span></span>](debugging-structures.md)
