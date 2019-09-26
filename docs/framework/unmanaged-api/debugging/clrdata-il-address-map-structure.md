---
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
ms.openlocfilehash: 3f6928832d822422177ebd7def142422953468a0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274287"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="6229c-102">CLRDATA_IL_ADDRESS_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="6229c-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="6229c-103">Bir Il 'yi eşlemek için bir Il tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6229c-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6229c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6229c-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="6229c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6229c-105">Members</span></span>

| <span data-ttu-id="6229c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6229c-106">Member</span></span>         | <span data-ttu-id="6229c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6229c-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="6229c-108">Kapsanan adres aralığı için Il kayması</span><span class="sxs-lookup"><span data-stu-id="6229c-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="6229c-109">Aralığın başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="6229c-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="6229c-110">Aralığın bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="6229c-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="6229c-111">Verilerin türü.</span><span class="sxs-lookup"><span data-stu-id="6229c-111">The type of the data.</span></span> <span data-ttu-id="6229c-112">Bu değer şu anda kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="6229c-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="6229c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6229c-113">Remarks</span></span>

<span data-ttu-id="6229c-114">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="6229c-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="6229c-115">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın; burada `CLRDATA_ADDRESS` 64 bitlik işaretsiz bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="6229c-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="6229c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6229c-116">Requirements</span></span>

<span data-ttu-id="6229c-117">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6229c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6229c-118">**Üst bilgi** Yok.</span><span class="sxs-lookup"><span data-stu-id="6229c-118">**Header:** None</span></span>  
<span data-ttu-id="6229c-119">**Kitaplığı** Yok.</span><span class="sxs-lookup"><span data-stu-id="6229c-119">**Library:** None</span></span>   
<span data-ttu-id="6229c-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6229c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6229c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6229c-121">See also</span></span>

- [<span data-ttu-id="6229c-122">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6229c-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="6229c-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6229c-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="6229c-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="6229c-124">Debugging Structures</span></span>](debugging-structures.md)
