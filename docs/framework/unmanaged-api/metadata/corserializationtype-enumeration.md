---
title: CorSerializationType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
ms.openlocfilehash: 649a9159f99afa64615c40c23a98a80318ae0d7f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009177"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="0a30e-102">CorSerializationType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0a30e-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="0a30e-103">Bir nesnenin ortak dil çalışma zamanı tarafından nasıl serileştirildiği belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a30e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a30e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="0a30e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0a30e-105">Members</span></span>  
  
|<span data-ttu-id="0a30e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0a30e-106">Member</span></span>|<span data-ttu-id="0a30e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a30e-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="0a30e-108">Nesnenin serileştirilmesi tanımsız.</span><span class="sxs-lookup"><span data-stu-id="0a30e-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="0a30e-109">Nesne, Boole türü olarak serileştirilir</span><span class="sxs-lookup"><span data-stu-id="0a30e-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="0a30e-110">Nesne bir karakter türü olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="0a30e-111">Nesne, işaretli bir 1 baytlık tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="0a30e-112">Nesne işaretsiz bir 1 baytlık tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="0a30e-113">Nesne, işaretli bir 2 baytlık tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="0a30e-114">Nesne işaretsiz bir 2 baytlık tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="0a30e-115">Nesne, imzalanmış 4 baytlık tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="0a30e-116">Nesne işaretsiz 4 baytlık tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="0a30e-117">Nesne, imzalanmış 8 baytlık tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="0a30e-118">Nesne işaretsiz 8 baytlık tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="0a30e-119">Nesne 4 baytlık kayan nokta olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="0a30e-120">Nesne 8 baytlık kayan nokta olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="0a30e-121">Nesne bir System. String türü olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="0a30e-122">Nesne tek boyutlu, sıfır alt sınır dizisi olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="0a30e-123">Nesne genel bir tür olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="0a30e-124">Nesne etiketli bir nesne olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="0a30e-125">Nesne bir alan olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="0a30e-126">Nesne bir özellik olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="0a30e-127">Nesne bir sabit listesi olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a30e-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a30e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a30e-128">Requirements</span></span>  
 <span data-ttu-id="0a30e-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a30e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a30e-130">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="0a30e-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0a30e-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a30e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a30e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a30e-132">See also</span></span>

- [<span data-ttu-id="0a30e-133">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="0a30e-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
