---
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
ms.openlocfilehash: 8eb841b4c4f06a3932805ae6222bdd693def5ea0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274307"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="363d0-102">CLRDATA_ADDRESS_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="363d0-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="363d0-103">Bir adres aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="363d0-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="363d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="363d0-104">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="363d0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="363d0-105">Members</span></span>

| <span data-ttu-id="363d0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="363d0-106">Member</span></span>         | <span data-ttu-id="363d0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="363d0-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="363d0-108">Aralığın başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="363d0-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="363d0-109">Aralığın bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="363d0-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="363d0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="363d0-110">Remarks</span></span>

<span data-ttu-id="363d0-111">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="363d0-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="363d0-112">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın; burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="363d0-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="363d0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="363d0-113">Requirements</span></span>

<span data-ttu-id="363d0-114">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="363d0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="363d0-115">**Üst bilgi** Yok.</span><span class="sxs-lookup"><span data-stu-id="363d0-115">**Header:** None</span></span>  
<span data-ttu-id="363d0-116">**Kitaplığı** Yok.</span><span class="sxs-lookup"><span data-stu-id="363d0-116">**Library:** None</span></span>  
<span data-ttu-id="363d0-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="363d0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="363d0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="363d0-118">See also</span></span>

- [<span data-ttu-id="363d0-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="363d0-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="363d0-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="363d0-120">Debugging Structures</span></span>](debugging-structures.md)
