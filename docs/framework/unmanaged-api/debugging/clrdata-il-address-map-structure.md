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
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179370"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="6bb14-102">CLRDATA_IL_ADDRESS_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="6bb14-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="6bb14-103">Adres eşleme için bir IL tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6bb14-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6bb14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bb14-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="6bb14-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6bb14-105">Members</span></span>

| <span data-ttu-id="6bb14-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6bb14-106">Member</span></span>         | <span data-ttu-id="6bb14-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bb14-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="6bb14-108">İçerdiği adres aralığı için IL ofset</span><span class="sxs-lookup"><span data-stu-id="6bb14-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="6bb14-109">Aralığın başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="6bb14-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="6bb14-110">Aralığın son adresi.</span><span class="sxs-lookup"><span data-stu-id="6bb14-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="6bb14-111">Verilerin türü.</span><span class="sxs-lookup"><span data-stu-id="6bb14-111">The type of the data.</span></span> <span data-ttu-id="6bb14-112">Bu değer şu anda kullanılmaz</span><span class="sxs-lookup"><span data-stu-id="6bb14-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="6bb14-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bb14-113">Remarks</span></span>

<span data-ttu-id="6bb14-114">Bu yapı çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="6bb14-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="6bb14-115">Kullanmak için, 64 bit imzasız `CLRDATA_ADDRESS` tamsayı olduğu yapıyı yukarıda belirtildiği gibi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6bb14-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="6bb14-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bb14-116">Requirements</span></span>

<span data-ttu-id="6bb14-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bb14-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6bb14-118">**Üstbilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6bb14-118">**Header:** None</span></span>  
<span data-ttu-id="6bb14-119">**Kütüphane:** Yok **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb14-119">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6bb14-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bb14-120">See also</span></span>

- [<span data-ttu-id="6bb14-121">CLRDataSourceType Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="6bb14-121">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="6bb14-122">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="6bb14-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="6bb14-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="6bb14-123">Debugging Structures</span></span>](debugging-structures.md)
