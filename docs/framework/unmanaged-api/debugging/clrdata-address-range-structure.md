---
description: 'Daha fazla bilgi edinin: CLRDATA_ADDRESS_RANGE yapısı'
title: CLRDATA_ADDRESS_RANGE Yapısı
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5d671a08064781b71756efc3c753468e6769d4ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662344"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="7c368-103">CLRDATA_ADDRESS_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="7c368-103">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="7c368-104">Bir adres aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c368-104">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7c368-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7c368-105">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="7c368-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7c368-106">Members</span></span>

| <span data-ttu-id="7c368-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7c368-107">Member</span></span>         | <span data-ttu-id="7c368-108">Description</span><span class="sxs-lookup"><span data-stu-id="7c368-108">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="7c368-109">Aralığın başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="7c368-109">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="7c368-110">Aralığın bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="7c368-110">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="7c368-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c368-111">Remarks</span></span>

<span data-ttu-id="7c368-112">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="7c368-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="7c368-113">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın; burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="7c368-113">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c368-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c368-114">Requirements</span></span>

<span data-ttu-id="7c368-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c368-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7c368-116">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7c368-116">**Header:** None</span></span>  
<span data-ttu-id="7c368-117">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7c368-117">**Library:** None</span></span>  
<span data-ttu-id="7c368-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7c368-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7c368-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c368-119">See also</span></span>

- [<span data-ttu-id="7c368-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7c368-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="7c368-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="7c368-121">Debugging Structures</span></span>](debugging-structures.md)
