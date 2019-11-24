---
title: CorThreadSafetyOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 93dd8c56176890d04d792f3c336492e4f232825b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442473"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="ce892-102">CorThreadSafetyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ce892-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="ce892-103">Specifies flags to select options for thread safety.</span><span class="sxs-lookup"><span data-stu-id="ce892-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce892-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce892-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="ce892-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ce892-105">Members</span></span>

|<span data-ttu-id="ce892-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ce892-106">Member</span></span>|<span data-ttu-id="ce892-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce892-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="ce892-108">Default value.</span><span class="sxs-lookup"><span data-stu-id="ce892-108">Default value.</span></span> <span data-ttu-id="ce892-109">Same as `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="ce892-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="ce892-110">Indicates that a reader/writer lock cannot be set.</span><span class="sxs-lookup"><span data-stu-id="ce892-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="ce892-111">Indicates that a reader/writer lock can be set.</span><span class="sxs-lookup"><span data-stu-id="ce892-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="ce892-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce892-112">Requirements</span></span>

<span data-ttu-id="ce892-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce892-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ce892-114">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ce892-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="ce892-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce892-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ce892-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce892-116">See also</span></span>

- [<span data-ttu-id="ce892-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ce892-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
