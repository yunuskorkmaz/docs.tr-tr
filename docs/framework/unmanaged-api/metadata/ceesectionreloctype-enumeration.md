---
description: 'Daha fazla bilgi edinin: CeeSectionRelocType numaralandırması'
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
ms.openlocfilehash: 49f7b39b3cc4c2e71dd3e4e426d0ca787e9ac0b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678841"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="8083f-103">CeeSectionRelocType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8083f-103">CeeSectionRelocType Enumeration</span></span>

<span data-ttu-id="8083f-104">`reloc` [ICeeGen:: AddSectionReloc](iceegen-addsectionreloc-method.md)çağrısında bulunan yönergenin türünü etkilemek için değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8083f-104">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8083f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8083f-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8083f-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8083f-106">Members</span></span>  
  
|<span data-ttu-id="8083f-107">Üye</span><span class="sxs-lookup"><span data-stu-id="8083f-107">Member</span></span>|<span data-ttu-id="8083f-108">Description</span><span class="sxs-lookup"><span data-stu-id="8083f-108">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="8083f-109">Yalnızca bir bölüm-göreli `reloc` , bir. reloc bölümü göndermek için bir öğe gönderir.</span><span class="sxs-lookup"><span data-stu-id="8083f-109">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="8083f-110">`reloc`İşaretçi boyutunda bir konum için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8083f-110">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="8083f-111">Bu, platforma bağlı olarak BASED_HIGHLOW veya BASED_DIR64 dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8083f-111">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="8083f-112">`reloc`32 bitlik bir sayının ilk 16 biti için bir oluşturur; burada alt 16 bit,. reloc tablosundaki sonraki sözcüğe dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="8083f-112">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="8083f-113">Bir. reloc bölümüne hiçbir şey göndermek için bir belirteç eşlemesi konum değişikliği üretir.</span><span class="sxs-lookup"><span data-stu-id="8083f-113">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="8083f-114">Değerin bir göreli adres düzeltmesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8083f-114">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="8083f-115">Yalnızca bir bölüm-göreli `reloc` , bir. reloc bölümü göndermek için bir öğe gönderir.</span><span class="sxs-lookup"><span data-stu-id="8083f-115">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="8083f-116">Bu, bölümün `reloc` sanal adresini değil, bölümünün dosya konumuyla ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="8083f-116">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="8083f-117">Kod göreli bir adres düzeltmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8083f-117">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="8083f-118">`reloc`IA64 yönergesinde 64 bitlik bir adres için bir üretir `movl` .</span><span class="sxs-lookup"><span data-stu-id="8083f-118">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="8083f-119">`reloc`64 bitlik bir adres için bir üretir.</span><span class="sxs-lookup"><span data-stu-id="8083f-119">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="8083f-120">`reloc`IA64 yönergesinde 25 BIT bilgisayar göreli adresi için oluşturun `br.call` .</span><span class="sxs-lookup"><span data-stu-id="8083f-120">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="8083f-121">`reloc`IA64 yönergesinde 64 bitlik BIR bilgisayar göreli adresi için bir üretir `brl.call` .</span><span class="sxs-lookup"><span data-stu-id="8083f-121">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="8083f-122">Etiketli işaretçi değerleri için kullanılan 30 bitlik bir bölüm-göreli oluşturur `reloc` .</span><span class="sxs-lookup"><span data-stu-id="8083f-122">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="8083f-123">Bu sabit listesine yapılan eklerin iç ad dizisine yansıtıldığından emin olmak için Sentinel değeri `reloc` .</span><span class="sxs-lookup"><span data-stu-id="8083f-123">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="8083f-124">Temel bir taban yaymamalıdır `reloc` .</span><span class="sxs-lookup"><span data-stu-id="8083f-124">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="8083f-125">Bellek ön düzeltme içeriğinin, Bölüm boşluğu yerine bir işaretçi olduğunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="8083f-125">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8083f-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8083f-126">Requirements</span></span>  

 <span data-ttu-id="8083f-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8083f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8083f-128">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8083f-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8083f-129">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8083f-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8083f-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8083f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8083f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8083f-131">See also</span></span>

- [<span data-ttu-id="8083f-132">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="8083f-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="8083f-133">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8083f-133">ICeeGen Interface</span></span>](iceegen-interface.md)
- [<span data-ttu-id="8083f-134">AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8083f-134">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)
