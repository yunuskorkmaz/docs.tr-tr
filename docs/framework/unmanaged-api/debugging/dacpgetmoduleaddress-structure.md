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
ms.openlocfilehash: cbea6c0562c68ae5d18247dc97bc53eb9dfbfd7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104116"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="1ac41-102">DacpGetModuleAddress yapısı</span><span class="sxs-lookup"><span data-stu-id="1ac41-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="1ac41-103">Bir modül adresi isteği için bir kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ac41-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1ac41-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ac41-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="1ac41-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1ac41-105">Members</span></span>

| <span data-ttu-id="1ac41-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1ac41-106">Member</span></span>      | <span data-ttu-id="1ac41-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ac41-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="1ac41-108">Modül işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1ac41-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="1ac41-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1ac41-109">Methods</span></span>

| <span data-ttu-id="1ac41-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1ac41-110">Method</span></span>                                                                                               | <span data-ttu-id="1ac41-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ac41-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="1ac41-112">İstek</span><span class="sxs-lookup"><span data-stu-id="1ac41-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="1ac41-113">Belirtilen çalışma zamanı yapısı yapısından doldurmak için bir istek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1ac41-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1ac41-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ac41-114">Remarks</span></span>

<span data-ttu-id="1ac41-115">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="1ac41-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1ac41-116">Bunu kullanmak için yapı, yukarıda belirtildiği gibi burada tanımlarsınız `CLRDATA_ADDRESS` 64-bit işaretsiz tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="1ac41-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ac41-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ac41-117">Requirements</span></span>
<span data-ttu-id="1ac41-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ac41-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1ac41-119">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="1ac41-119">**Header:** None</span></span>  
<span data-ttu-id="1ac41-120">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="1ac41-120">**Library:** None</span></span>  
<span data-ttu-id="1ac41-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1ac41-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1ac41-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ac41-122">See also</span></span>

- [<span data-ttu-id="1ac41-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1ac41-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="1ac41-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="1ac41-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
