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
ms.openlocfilehash: 78b30f624bd71234e8f1b56600b3a23d15fdf517
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006042"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="8b6fb-102">CeeSectionRelocType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8b6fb-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="8b6fb-103">`reloc` [ICeeGen:: AddSectionReloc](iceegen-addsectionreloc-method.md)çağrısında bulunan yönergenin türünü etkilemek için değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b6fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b6fb-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8b6fb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8b6fb-105">Members</span></span>  
  
|<span data-ttu-id="8b6fb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8b6fb-106">Member</span></span>|<span data-ttu-id="8b6fb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b6fb-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="8b6fb-108">Yalnızca bir bölüm-göreli `reloc` , bir. reloc bölümü göndermek için bir öğe gönderir.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="8b6fb-109">`reloc`İşaretçi boyutunda bir konum için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="8b6fb-110">Bu, platforma bağlı olarak BASED_HIGHLOW veya BASED_DIR64 dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="8b6fb-111">`reloc`32 bitlik bir sayının ilk 16 biti için bir oluşturur; burada alt 16 bit,. reloc tablosundaki sonraki sözcüğe dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="8b6fb-112">Bir. reloc bölümüne hiçbir şey göndermek için bir belirteç eşlemesi konum değişikliği üretir.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="8b6fb-113">Değerin bir göreli adres düzeltmesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="8b6fb-114">Yalnızca bir bölüm-göreli `reloc` , bir. reloc bölümü göndermek için bir öğe gönderir.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="8b6fb-115">Bu, bölümün `reloc` sanal adresini değil, bölümünün dosya konumuyla ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="8b6fb-116">Kod göreli bir adres düzeltmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="8b6fb-117">`reloc`IA64 yönergesinde 64 bitlik bir adres için bir üretir `movl` .</span><span class="sxs-lookup"><span data-stu-id="8b6fb-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="8b6fb-118">`reloc`64 bitlik bir adres için bir üretir.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="8b6fb-119">`reloc`IA64 yönergesinde 25 BIT bilgisayar göreli adresi için oluşturun `br.call` .</span><span class="sxs-lookup"><span data-stu-id="8b6fb-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="8b6fb-120">`reloc`IA64 yönergesinde 64 bitlik BIR bilgisayar göreli adresi için bir üretir `brl.call` .</span><span class="sxs-lookup"><span data-stu-id="8b6fb-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="8b6fb-121">Etiketli işaretçi değerleri için kullanılan 30 bitlik bir bölüm-göreli oluşturur `reloc` .</span><span class="sxs-lookup"><span data-stu-id="8b6fb-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="8b6fb-122">Bu sabit listesine yapılan eklerin iç ad dizisine yansıtıldığından emin olmak için Sentinel değeri `reloc` .</span><span class="sxs-lookup"><span data-stu-id="8b6fb-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="8b6fb-123">Temel bir taban yaymamalıdır `reloc` .</span><span class="sxs-lookup"><span data-stu-id="8b6fb-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="8b6fb-124">Bellek ön düzeltme içeriğinin, Bölüm boşluğu yerine bir işaretçi olduğunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b6fb-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b6fb-125">Requirements</span></span>  
 <span data-ttu-id="8b6fb-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b6fb-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b6fb-127">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8b6fb-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b6fb-128">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8b6fb-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b6fb-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b6fb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6fb-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b6fb-130">See also</span></span>

- [<span data-ttu-id="8b6fb-131">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="8b6fb-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="8b6fb-132">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b6fb-132">ICeeGen Interface</span></span>](iceegen-interface.md)
- [<span data-ttu-id="8b6fb-133">AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6fb-133">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)
