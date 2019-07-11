---
title: CLRDataSourceType numaralandırması
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d26cf45a0243d61757af5d9d0c00cf135ae15bdf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740862"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="febdd-102">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="febdd-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="febdd-103">CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="febdd-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="febdd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="febdd-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="febdd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="febdd-105">Members</span></span>

| <span data-ttu-id="febdd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="febdd-106">Member</span></span>                        | <span data-ttu-id="febdd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="febdd-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="febdd-108">Başka bir şey geçerli olduğunu belirtmek için</span><span class="sxs-lookup"><span data-stu-id="febdd-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="febdd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="febdd-109">Remarks</span></span>

<span data-ttu-id="febdd-110">Bu numaralandırma, çalışma zamanı içinde yaşar ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="febdd-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="febdd-111">Bunu kullanmak için yukarıda kodunuzda tanımlandığı gibi bir sabit listesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="febdd-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="febdd-112">Bu diğer adı için de geçerlidir `CLRDATA_ENUM` belirtildiği gibi [ortak veri türleri](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="febdd-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="febdd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="febdd-113">Requirements</span></span>

<span data-ttu-id="febdd-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="febdd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="febdd-115">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="febdd-115">**Header:** None</span></span>  
<span data-ttu-id="febdd-116">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="febdd-116">**Library:** None</span></span>  
<span data-ttu-id="febdd-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="febdd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="febdd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="febdd-118">See also</span></span>

- [<span data-ttu-id="febdd-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="febdd-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="febdd-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="febdd-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
