---
title: CeeSectionRelocType Numaralandırması
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176220"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="48835-102">CeeSectionRelocType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="48835-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="48835-103">`reloc` [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)için bir çağrıda yayılan talimat türünü etkilemek için değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="48835-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48835-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48835-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="48835-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="48835-105">Members</span></span>  
  
|<span data-ttu-id="48835-106">Üye</span><span class="sxs-lookup"><span data-stu-id="48835-106">Member</span></span>|<span data-ttu-id="48835-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48835-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="48835-108">Yalnızca bir bölüm görelisi `reloc`oluşturur, .reloc bölümüne hiçbir şey göndermez.</span><span class="sxs-lookup"><span data-stu-id="48835-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="48835-109">İşaretçi `reloc` boyutunda bir konum için bir konum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48835-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="48835-110">Bu platforma bağlı olarak BASED_HIGHLOW veya BASED_DIR64 dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="48835-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="48835-111">32 `reloc` bitlik bir sayının en üst 16 biti için bir sayı oluşturur ve burada en alttaki 16 bit .reloc tablosundaki bir sonraki sözcükte yer eder.</span><span class="sxs-lookup"><span data-stu-id="48835-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="48835-112">Bir .reloc bölümüne hiçbir şey göndermeden bir belirteç eşemi yer değiştirme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48835-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="48835-113">Değerin göreceli bir adres düzeltmesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="48835-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="48835-114">Yalnızca bir bölüm görelisi `reloc`oluşturur, .reloc bölümüne hiçbir şey göndermez.</span><span class="sxs-lookup"><span data-stu-id="48835-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="48835-115">Bu, `reloc` bölümün sanal adresine değil, bölümün dosya konumuna göredir.</span><span class="sxs-lookup"><span data-stu-id="48835-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="48835-116">Kod göreli adres düzeltmesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="48835-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="48835-117">`reloc` ia64 `movl` yönergesinde 64 bitlik bir adres oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48835-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="48835-118">64 `reloc` bitlik bir adres oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48835-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="48835-119">ia64 `reloc` `br.call` yönergesinde 25 bit PC göreli bir adres için bir adres oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48835-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="48835-120">ia64 `reloc` `brl.call` yönergesinde 64 bit PC göreli bir adres oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48835-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="48835-121">Etiketlenmiş işaretçi değerleri için `reloc`kullanılan 30 bitlik bir bölüm görelisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48835-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="48835-122">Bu enum a eklemeler iç `reloc` ad dizisine yansıtılır sağlamak için bir sentinel değeri.</span><span class="sxs-lookup"><span data-stu-id="48835-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="48835-123">Bir baz `reloc`yayan değil belirtir.</span><span class="sxs-lookup"><span data-stu-id="48835-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="48835-124">Belleğin ön düzeltme içeriğinin bir bölüm ofset yerine işaretçi olduğunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="48835-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="48835-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48835-125">Requirements</span></span>  
 <span data-ttu-id="48835-126">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48835-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48835-127">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="48835-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48835-128">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="48835-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48835-129">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48835-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48835-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48835-130">See also</span></span>

- [<span data-ttu-id="48835-131">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="48835-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="48835-132">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48835-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="48835-133">AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48835-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
