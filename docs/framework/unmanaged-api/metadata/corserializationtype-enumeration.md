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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4959d595030df476f5554841c2ae3c73a86a2c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446665"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="c009b-102">CorSerializationType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c009b-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="c009b-103">Bir nesne ortak dil çalışma zamanı tarafından nasıl serileştirilmiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="c009b-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c009b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c009b-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="c009b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c009b-105">Members</span></span>  
  
|<span data-ttu-id="c009b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c009b-106">Member</span></span>|<span data-ttu-id="c009b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c009b-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="c009b-108">Nesnenin seri hale getirme tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c009b-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="c009b-109">Boolean türünde nesne seri hale getirilmiş</span><span class="sxs-lookup"><span data-stu-id="c009b-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="c009b-110">Nesne bir karakter türü olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="c009b-111">Nesne imzalı 1-bayt tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="c009b-112">Nesne imzasız 1-bayt tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="c009b-113">Nesne olarak imzalanmış bir 2-bayt tamsayı serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="c009b-114">Nesne imzasız 2-bayt tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="c009b-115">Nesne imzalı 4-bayt tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="c009b-116">Nesne imzasız 4-bayt tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="c009b-117">Nesne işaretli 8-bayt tamsayı serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="c009b-118">Nesne imzasız 8-bayt tamsayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="c009b-119">Nesne 4-bayt kayan nokta serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="c009b-120">Nesne 8-bayt kayan nokta serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="c009b-121">Nesne System.String türünde serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="c009b-122">Nesne seri hale getirilmiş bir tek boyutlu, sıfır alt sınır dizi.</span><span class="sxs-lookup"><span data-stu-id="c009b-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="c009b-123">Nesne genel bir tür serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="c009b-124">Nesne etiketli bir nesne olarak seri değildir.</span><span class="sxs-lookup"><span data-stu-id="c009b-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="c009b-125">Nesne bir alan olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="c009b-126">Nesne bir özellik olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="c009b-127">Nesne sabit olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="c009b-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c009b-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c009b-128">Requirements</span></span>  
 <span data-ttu-id="c009b-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c009b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c009b-130">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c009b-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c009b-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c009b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c009b-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c009b-132">See Also</span></span>  
 [<span data-ttu-id="c009b-133">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c009b-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
