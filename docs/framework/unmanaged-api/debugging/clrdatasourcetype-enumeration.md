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
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274102"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="88de4-102">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="88de4-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="88de4-103">CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="88de4-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="88de4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88de4-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="88de4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="88de4-105">Members</span></span>

| <span data-ttu-id="88de4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="88de4-106">Member</span></span>                        | <span data-ttu-id="88de4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88de4-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="88de4-108">Başka hiçbir şeyin uygulanacağını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="88de4-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="88de4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88de4-109">Remarks</span></span>

<span data-ttu-id="88de4-110">Bu numaralandırma çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="88de4-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="88de4-111">Kullanmak için, kodunuzda yukarıda tanımlanan bir sabit listesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="88de4-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="88de4-112">Bu, `CLRDATA_ENUM` [ortak veri türlerinde](../common-data-types-unmanaged-api-reference.md)bahsedildiği gibi, için de başka bir ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="88de4-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="88de4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88de4-113">Requirements</span></span>

<span data-ttu-id="88de4-114">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88de4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="88de4-115">**Üst bilgi** Yok.</span><span class="sxs-lookup"><span data-stu-id="88de4-115">**Header:** None</span></span>  
<span data-ttu-id="88de4-116">**Kitaplığı** Yok.</span><span class="sxs-lookup"><span data-stu-id="88de4-116">**Library:** None</span></span>  
<span data-ttu-id="88de4-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="88de4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="88de4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88de4-118">See also</span></span>

- [<span data-ttu-id="88de4-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="88de4-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="88de4-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="88de4-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
