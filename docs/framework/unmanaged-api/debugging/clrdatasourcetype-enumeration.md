---
description: 'Hakkında daha fazla bilgi edinin: CLRDataSourceType numaralandırması'
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
ms.openlocfilehash: 06590e21aa4cdf6e89977a79da36a413d5ff4f1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747248"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="c11a9-103">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c11a9-103">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="c11a9-104">CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c11a9-104">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c11a9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c11a9-105">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="c11a9-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c11a9-106">Members</span></span>

| <span data-ttu-id="c11a9-107">Üye</span><span class="sxs-lookup"><span data-stu-id="c11a9-107">Member</span></span>                        | <span data-ttu-id="c11a9-108">Description</span><span class="sxs-lookup"><span data-stu-id="c11a9-108">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="c11a9-109">Başka hiçbir şeyin uygulanacağını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c11a9-109">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="c11a9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c11a9-110">Remarks</span></span>

<span data-ttu-id="c11a9-111">Bu numaralandırma çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="c11a9-111">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c11a9-112">Kullanmak için, kodunuzda yukarıda tanımlanan bir sabit listesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c11a9-112">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="c11a9-113">Bu, `CLRDATA_ENUM` [ortak veri türlerinde](../common-data-types-unmanaged-api-reference.md)bahsedildiği gibi, için de başka bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="c11a9-113">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c11a9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c11a9-114">Requirements</span></span>

<span data-ttu-id="c11a9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c11a9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c11a9-116">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="c11a9-116">**Header:** None</span></span>  
<span data-ttu-id="c11a9-117">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="c11a9-117">**Library:** None</span></span>  
<span data-ttu-id="c11a9-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c11a9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c11a9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c11a9-119">See also</span></span>

- [<span data-ttu-id="c11a9-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c11a9-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="c11a9-121">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c11a9-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
