---
title: DacpGetModuleAddress yapısı
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
ms.openlocfilehash: 1e3a62de3259c012438c64ece26e696682ec96e6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789199"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="1babd-102">DacpGetModuleAddress yapısı</span><span class="sxs-lookup"><span data-stu-id="1babd-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="1babd-103">Modül adresi isteği için kapsayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1babd-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1babd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1babd-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="1babd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1babd-105">Members</span></span>

| <span data-ttu-id="1babd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1babd-106">Member</span></span>      | <span data-ttu-id="1babd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1babd-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="1babd-108">Modülün işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1babd-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="1babd-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1babd-109">Methods</span></span>

| <span data-ttu-id="1babd-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1babd-110">Method</span></span>                                                                                               | <span data-ttu-id="1babd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1babd-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="1babd-112">İstek</span><span class="sxs-lookup"><span data-stu-id="1babd-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="1babd-113">Yapıyı verilen çalışma zamanı yapısından doldurma isteği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1babd-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1babd-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1babd-114">Remarks</span></span>

<span data-ttu-id="1babd-115">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="1babd-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1babd-116">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın, burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="1babd-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="1babd-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1babd-117">Requirements</span></span>
<span data-ttu-id="1babd-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1babd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1babd-119">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1babd-119">**Header:** None</span></span>  
<span data-ttu-id="1babd-120">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1babd-120">**Library:** None</span></span>  
<span data-ttu-id="1babd-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1babd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1babd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1babd-122">See also</span></span>

- [<span data-ttu-id="1babd-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1babd-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="1babd-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="1babd-124">Debugging Structures</span></span>](debugging-structures.md)
