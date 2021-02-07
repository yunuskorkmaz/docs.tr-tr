---
description: 'Daha fazla bilgi edinin: CorThreadSafetyOptions numaralandırması'
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
ms.openlocfilehash: 7915bcf5e7b71fa84ea83642467c1600cd38712d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707325"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="ca3a2-103">CorThreadSafetyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ca3a2-103">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="ca3a2-104">İş parçacığı güvenliği seçeneklerinin seçilecek bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca3a2-104">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca3a2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca3a2-105">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="ca3a2-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ca3a2-106">Members</span></span>

|<span data-ttu-id="ca3a2-107">Üye</span><span class="sxs-lookup"><span data-stu-id="ca3a2-107">Member</span></span>|<span data-ttu-id="ca3a2-108">Description</span><span class="sxs-lookup"><span data-stu-id="ca3a2-108">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="ca3a2-109">Varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="ca3a2-109">Default value.</span></span> <span data-ttu-id="ca3a2-110">Aynı `MDThreadSafetyOff` .</span><span class="sxs-lookup"><span data-stu-id="ca3a2-110">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="ca3a2-111">Bir okuyucu/yazıcı kilidinin ayarlanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca3a2-111">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="ca3a2-112">Bir okuyucu/yazıcı kilidinin ayarlanamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca3a2-112">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="ca3a2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca3a2-113">Requirements</span></span>

<span data-ttu-id="ca3a2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca3a2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ca3a2-115">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="ca3a2-115">**Header:** CorHdr.h</span></span>

<span data-ttu-id="ca3a2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca3a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ca3a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca3a2-117">See also</span></span>

- [<span data-ttu-id="ca3a2-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="ca3a2-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
