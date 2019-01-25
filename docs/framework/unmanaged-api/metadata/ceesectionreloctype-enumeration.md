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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1541c6fa2b1d307fc8e854a67b7cc3068b7bb4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580726"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="bc2e6-102">CeeSectionRelocType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bc2e6-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="bc2e6-103">Türünü etkilemek için değerler sağlayan `reloc` çağrıda yayılan yönerge [Iceegen::addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="bc2e6-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc2e6-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="bc2e6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bc2e6-105">Members</span></span>  
  
|<span data-ttu-id="bc2e6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bc2e6-106">Member</span></span>|<span data-ttu-id="bc2e6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc2e6-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="bc2e6-108">Yalnızca bir bölüm göreli oluşturur `reloc`, gönderen bir .reloc bölüme hiçbir şey yok.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="bc2e6-109">Oluşturur bir `reloc` işaretçi boyutlu konumu.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="bc2e6-110">Platforma bağlı olarak bu BASED_HIGHLOW ya da BASED_DIR64 dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="bc2e6-111">Oluşturur bir `reloc` üst burada alt 16 bit dahil edilecek .reloc tabloda sonraki sözcüğe 32 bit sayı, 16 bit için.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="bc2e6-112">Hiçbir şey .reloc bölüme gönderirken bir belirteç Haritası yeniden konumlandırma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="bc2e6-113">Göreli adres düzeltme değeri olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="bc2e6-114">Yalnızca bir bölüm göreli oluşturur `reloc`, gönderen bir .reloc bölüme hiçbir şey yok.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="bc2e6-115">Bu `reloc` bölümünde, sanal adres bölümün göreli dosya konumu.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="bc2e6-116">Bir kod göreli adres düzeltmesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="bc2e6-117">Oluşturur bir `reloc` bir IA64 bir 64 bit adresi `movl` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="bc2e6-118">Oluşturur bir `reloc` 64-bit adresi.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="bc2e6-119">Oluşturmak bir `reloc` bir IA64 25-bit bir PC göreli adresi `br.call` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="bc2e6-120">Oluşturur bir `reloc` bir IA64 bir 64 bit bilgisayar göreli adresi `brl.call` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="bc2e6-121">30 bit'lik bir bölümü-göreli oluşturur `reloc`etiketli işaretçi değerleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="bc2e6-122">Bu sabit listesi üzerindeki herhangi bir ek sağlamaya yardımcı olmak için bir sentinel değer iç ağa yansıtılır `reloc` ad dizisi.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="bc2e6-123">Temel yayma değil belirtir `reloc`.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="bc2e6-124">Bellek öncesi düzeltme içeriğinin bir bölüm yerine bir işaretçi olduğunu belirten bir değer uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc2e6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc2e6-125">Requirements</span></span>  
 <span data-ttu-id="bc2e6-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc2e6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc2e6-127">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bc2e6-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc2e6-128">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bc2e6-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc2e6-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc2e6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2e6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc2e6-130">See also</span></span>
- [<span data-ttu-id="bc2e6-131">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="bc2e6-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="bc2e6-132">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc2e6-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="bc2e6-133">AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc2e6-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
