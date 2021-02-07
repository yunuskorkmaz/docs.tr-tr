---
description: 'Daha fazla bilgi edinin: DacpGetModuleAddress yapısı'
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
ms.openlocfilehash: 3de76cc4f15bffd35d7a43ae25a313eb2fe59b82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661603"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="3cbfc-103">DacpGetModuleAddress Yapısı</span><span class="sxs-lookup"><span data-stu-id="3cbfc-103">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="3cbfc-104">Modül adresi isteği için kapsayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3cbfc-104">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3cbfc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3cbfc-105">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="3cbfc-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3cbfc-106">Members</span></span>

| <span data-ttu-id="3cbfc-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3cbfc-107">Member</span></span>      | <span data-ttu-id="3cbfc-108">Description</span><span class="sxs-lookup"><span data-stu-id="3cbfc-108">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="3cbfc-109">Modülün işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3cbfc-109">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="3cbfc-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3cbfc-110">Methods</span></span>

| <span data-ttu-id="3cbfc-111">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3cbfc-111">Method</span></span>                                                                                               | <span data-ttu-id="3cbfc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cbfc-112">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="3cbfc-113">İstek</span><span class="sxs-lookup"><span data-stu-id="3cbfc-113">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="3cbfc-114">Yapıyı verilen çalışma zamanı yapısından doldurma isteği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3cbfc-114">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3cbfc-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cbfc-115">Remarks</span></span>

<span data-ttu-id="3cbfc-116">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="3cbfc-116">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3cbfc-117">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın; burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="3cbfc-117">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="3cbfc-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cbfc-118">Requirements</span></span>

<span data-ttu-id="3cbfc-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cbfc-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3cbfc-120">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="3cbfc-120">**Header:** None</span></span>  
<span data-ttu-id="3cbfc-121">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="3cbfc-121">**Library:** None</span></span>  
<span data-ttu-id="3cbfc-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3cbfc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3cbfc-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cbfc-123">See also</span></span>

- [<span data-ttu-id="3cbfc-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3cbfc-124">Debugging</span></span>](index.md)
- [<span data-ttu-id="3cbfc-125">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="3cbfc-125">Debugging Structures</span></span>](debugging-structures.md)
