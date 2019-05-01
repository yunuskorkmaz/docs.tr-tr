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
ms.openlocfilehash: 3aac7e24fa9cd03350aebf5f441063bcedfaed04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961297"
---
# <a name="clrdatailaddressmap-structure"></a><span data-ttu-id="79f84-102">CLRDATA_IL_ADDRESS_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="79f84-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="79f84-103">Bir IL adresi eşleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79f84-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="79f84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79f84-104">Syntax</span></span>

```
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="79f84-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="79f84-105">Members</span></span>

| <span data-ttu-id="79f84-106">Üye</span><span class="sxs-lookup"><span data-stu-id="79f84-106">Member</span></span>         | <span data-ttu-id="79f84-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79f84-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="79f84-108">Kapsanan adresi aralığı için IL uzaklığı</span><span class="sxs-lookup"><span data-stu-id="79f84-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="79f84-109">Aralığın başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="79f84-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="79f84-110">Aralığın bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="79f84-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="79f84-111">Veri türü.</span><span class="sxs-lookup"><span data-stu-id="79f84-111">The type of the data.</span></span> <span data-ttu-id="79f84-112">Bu değer şu anda kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="79f84-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="79f84-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79f84-113">Remarks</span></span>

<span data-ttu-id="79f84-114">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="79f84-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="79f84-115">Bunu kullanmak için yapı, yukarıda belirtildiği gibi burada tanımlarsınız `CLRDATA_ADDRESS` 64-bit işaretsiz tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="79f84-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="79f84-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79f84-116">Requirements</span></span>

<span data-ttu-id="79f84-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79f84-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="79f84-118">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="79f84-118">**Header:** None</span></span>  
<span data-ttu-id="79f84-119">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="79f84-119">**Library:** None</span></span>   
<span data-ttu-id="79f84-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="79f84-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="79f84-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79f84-121">See also</span></span>

- [<span data-ttu-id="79f84-122">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="79f84-122">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="79f84-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="79f84-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="79f84-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="79f84-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
