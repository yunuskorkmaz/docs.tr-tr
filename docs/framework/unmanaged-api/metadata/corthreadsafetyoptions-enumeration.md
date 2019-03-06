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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d71d2a5b3007d4e877900443af426a9643b29125
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360449"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="d2ded-102">CorThreadSafetyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d2ded-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="d2ded-103">İş parçacığı güvenliği seçeneklerini seçmek için bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2ded-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2ded-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2ded-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="d2ded-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d2ded-105">Members</span></span>

|<span data-ttu-id="d2ded-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d2ded-106">Member</span></span>|<span data-ttu-id="d2ded-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2ded-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="d2ded-108">Varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="d2ded-108">Default value.</span></span> <span data-ttu-id="d2ded-109">Aynı `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="d2ded-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="d2ded-110">Bir Okuyucu/Yazıcı kilidi ayarlanamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2ded-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="d2ded-111">Bir Okuyucu/Yazıcı kilidi ayarlanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2ded-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="d2ded-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2ded-112">Requirements</span></span>

<span data-ttu-id="d2ded-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2ded-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="d2ded-114">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d2ded-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="d2ded-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2ded-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d2ded-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2ded-116">See also</span></span>

- [<span data-ttu-id="d2ded-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d2ded-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
