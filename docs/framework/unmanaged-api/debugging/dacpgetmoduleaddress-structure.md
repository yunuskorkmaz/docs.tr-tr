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
ms.openlocfilehash: e460264e2393858c028ba51aec4a4f2c01649994
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860832"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="bb6d2-102">DacpGetModuleAddress Yapısı</span><span class="sxs-lookup"><span data-stu-id="bb6d2-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="bb6d2-103">Modül adresi isteği için kapsayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bb6d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb6d2-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="bb6d2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bb6d2-105">Members</span></span>

| <span data-ttu-id="bb6d2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bb6d2-106">Member</span></span>      | <span data-ttu-id="bb6d2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6d2-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="bb6d2-108">Modülün işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="bb6d2-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bb6d2-109">Methods</span></span>

| <span data-ttu-id="bb6d2-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb6d2-110">Method</span></span>                                                                                               | <span data-ttu-id="bb6d2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb6d2-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="bb6d2-112">İstek</span><span class="sxs-lookup"><span data-stu-id="bb6d2-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="bb6d2-113">Yapıyı verilen çalışma zamanı yapısından doldurma isteği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bb6d2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb6d2-114">Remarks</span></span>

<span data-ttu-id="bb6d2-115">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="bb6d2-116">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın; burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb6d2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb6d2-117">Requirements</span></span>
<span data-ttu-id="bb6d2-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb6d2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bb6d2-119">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="bb6d2-119">**Header:** None</span></span>  
<span data-ttu-id="bb6d2-120">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="bb6d2-120">**Library:** None</span></span>  
<span data-ttu-id="bb6d2-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6d2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bb6d2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb6d2-122">See also</span></span>

- [<span data-ttu-id="bb6d2-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bb6d2-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="bb6d2-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="bb6d2-124">Debugging Structures</span></span>](debugging-structures.md)
