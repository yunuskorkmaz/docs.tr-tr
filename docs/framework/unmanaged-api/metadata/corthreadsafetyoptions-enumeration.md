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
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="94567-102">CorThreadSafetyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="94567-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="94567-103">İş parçacığı güvenliği seçeneklerinin seçilecek bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="94567-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="94567-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94567-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="94567-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="94567-105">Members</span></span>

|<span data-ttu-id="94567-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="94567-106">Member</span></span>|<span data-ttu-id="94567-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94567-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="94567-108">Varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="94567-108">Default value.</span></span> <span data-ttu-id="94567-109">`MDThreadSafetyOff`ile aynı.</span><span class="sxs-lookup"><span data-stu-id="94567-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="94567-110">Bir okuyucu/yazıcı kilidinin ayarlanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="94567-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="94567-111">Bir okuyucu/yazıcı kilidinin ayarlanamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94567-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="94567-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94567-112">Requirements</span></span>

<span data-ttu-id="94567-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94567-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="94567-114">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="94567-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="94567-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94567-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="94567-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94567-116">See also</span></span>

- [<span data-ttu-id="94567-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="94567-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
