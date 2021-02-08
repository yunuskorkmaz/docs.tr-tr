---
description: 'Daha fazla bilgi edinin: CLRDATA_IL_ADDRESS_MAP yapısı'
title: CLRDATA_IL_ADDRESS_MAP Yapısı
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 02ee14154de0c1609e58cf6a2ad1ca62710567f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801858"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="5eb6d-103">CLRDATA_IL_ADDRESS_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="5eb6d-103">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="5eb6d-104">Bir Il 'yi eşlemek için bir Il tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5eb6d-104">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5eb6d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5eb6d-105">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="5eb6d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5eb6d-106">Members</span></span>

| <span data-ttu-id="5eb6d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5eb6d-107">Member</span></span>         | <span data-ttu-id="5eb6d-108">Description</span><span class="sxs-lookup"><span data-stu-id="5eb6d-108">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="5eb6d-109">Kapsanan adres aralığı için Il kayması</span><span class="sxs-lookup"><span data-stu-id="5eb6d-109">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="5eb6d-110">Aralığın başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="5eb6d-110">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="5eb6d-111">Aralığın bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="5eb6d-111">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="5eb6d-112">Verilerin türü.</span><span class="sxs-lookup"><span data-stu-id="5eb6d-112">The type of the data.</span></span> <span data-ttu-id="5eb6d-113">Bu değer şu anda kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="5eb6d-113">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="5eb6d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5eb6d-114">Remarks</span></span>

<span data-ttu-id="5eb6d-115">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="5eb6d-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="5eb6d-116">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın; burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="5eb6d-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="5eb6d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5eb6d-117">Requirements</span></span>

<span data-ttu-id="5eb6d-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5eb6d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5eb6d-119">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="5eb6d-119">**Header:** None</span></span>  
<span data-ttu-id="5eb6d-120">**Kitaplık:** Hiçbiri **.NET Framework sürümler:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5eb6d-120">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5eb6d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5eb6d-121">See also</span></span>

- [<span data-ttu-id="5eb6d-122">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5eb6d-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="5eb6d-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5eb6d-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="5eb6d-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="5eb6d-124">Debugging Structures</span></span>](debugging-structures.md)
