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
ms.openlocfilehash: c8b3f338659e2784db8deca3e1776e7926c30c32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506091"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="92ccd-102">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="92ccd-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="92ccd-103">CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="92ccd-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="92ccd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92ccd-104">Syntax</span></span>

```
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="92ccd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="92ccd-105">Members</span></span>

| <span data-ttu-id="92ccd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="92ccd-106">Member</span></span>                        | <span data-ttu-id="92ccd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92ccd-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="92ccd-108">Başka bir şey geçerli olduğunu belirtmek için</span><span class="sxs-lookup"><span data-stu-id="92ccd-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="92ccd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92ccd-109">Remarks</span></span>

<span data-ttu-id="92ccd-110">Bu numaralandırma, çalışma zamanı içinde yaşar ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="92ccd-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="92ccd-111">Bunu kullanmak için yukarıda kodunuzda tanımlandığı gibi bir sabit listesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="92ccd-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="92ccd-112">Bu diğer adı için de geçerlidir `CLRDATA_ENUM` belirtildiği gibi [ortak veri türleri](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="92ccd-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="92ccd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92ccd-113">Requirements</span></span>

<span data-ttu-id="92ccd-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92ccd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="92ccd-115">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="92ccd-115">**Header:** None</span></span>  
<span data-ttu-id="92ccd-116">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="92ccd-116">**Library:** None</span></span>  
<span data-ttu-id="92ccd-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="92ccd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="92ccd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92ccd-118">See also</span></span>

- [<span data-ttu-id="92ccd-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="92ccd-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="92ccd-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="92ccd-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
