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
ms.openlocfilehash: 484ca79483fc4a5d8f0d1cf2cd5a961c297249e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961323"
---
# <a name="clrdataaddressrange-structure"></a><span data-ttu-id="60d31-102">CLRDATA_ADDRESS_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="60d31-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="60d31-103">Bir adres aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60d31-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="60d31-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60d31-104">Syntax</span></span>

```
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="60d31-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="60d31-105">Members</span></span>

| <span data-ttu-id="60d31-106">Üye</span><span class="sxs-lookup"><span data-stu-id="60d31-106">Member</span></span>         | <span data-ttu-id="60d31-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60d31-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="60d31-108">Aralığın başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="60d31-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="60d31-109">Aralığın bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="60d31-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="60d31-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60d31-110">Remarks</span></span>

<span data-ttu-id="60d31-111">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="60d31-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="60d31-112">Bunu kullanmak için yapı, yukarıda belirtildiği gibi burada tanımlarsınız `CLRDATA_ADDRESS` 64-bit işaretsiz tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="60d31-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="60d31-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60d31-113">Requirements</span></span>

<span data-ttu-id="60d31-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60d31-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="60d31-115">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="60d31-115">**Header:** None</span></span>  
<span data-ttu-id="60d31-116">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="60d31-116">**Library:** None</span></span>  
<span data-ttu-id="60d31-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60d31-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="60d31-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60d31-118">See also</span></span>

- [<span data-ttu-id="60d31-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="60d31-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="60d31-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="60d31-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
