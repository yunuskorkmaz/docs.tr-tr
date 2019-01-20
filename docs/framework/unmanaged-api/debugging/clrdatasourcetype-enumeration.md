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
ms.openlocfilehash: 36651de5053e994103f79c9021e8e18e126f91fa
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416131"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="05dc1-102">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="05dc1-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="05dc1-103">CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="05dc1-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="05dc1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05dc1-104">Syntax</span></span>

```
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="05dc1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="05dc1-105">Members</span></span>

| <span data-ttu-id="05dc1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="05dc1-106">Member</span></span>                        | <span data-ttu-id="05dc1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05dc1-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="05dc1-108">Başka bir şey geçerli olduğunu belirtmek için</span><span class="sxs-lookup"><span data-stu-id="05dc1-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="05dc1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05dc1-109">Remarks</span></span>

<span data-ttu-id="05dc1-110">Bu numaralandırma, çalışma zamanı içinde yaşar ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="05dc1-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="05dc1-111">Bunu kullanmak için yukarıda kodunuzda tanımlandığı gibi bir sabit listesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="05dc1-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="05dc1-112">Bu diğer adı için de geçerlidir `CLRDATA_ENUM` belirtildiği gibi [ortak veri türleri](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="05dc1-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="05dc1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05dc1-113">Requirements</span></span>

<span data-ttu-id="05dc1-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05dc1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="05dc1-115">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="05dc1-115">**Header:** None</span></span>  
<span data-ttu-id="05dc1-116">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="05dc1-116">**Library:** None</span></span>  
<span data-ttu-id="05dc1-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="05dc1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="05dc1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05dc1-118">See Also</span></span>

- [<span data-ttu-id="05dc1-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="05dc1-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="05dc1-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="05dc1-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
