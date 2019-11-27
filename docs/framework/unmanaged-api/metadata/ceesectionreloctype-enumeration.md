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
ms.openlocfilehash: efce0c13944b383c42cbff6a6af4795293ee2989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444163"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="d8b17-102">CeeSectionRelocType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d8b17-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="d8b17-103">[ICeeGen:: AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)çağrısında yayılan `reloc` yönergesinin türünü etkilemek için değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8b17-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b17-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8b17-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d8b17-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="d8b17-105">Members</span></span>  
  
|<span data-ttu-id="d8b17-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="d8b17-106">Member</span></span>|<span data-ttu-id="d8b17-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8b17-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="d8b17-108">Bir. reloc bölümüne hiçbir şey göndermek için yalnızca bölüm göreli bir `reloc`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8b17-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="d8b17-109">İşaretçi boyutunda bir konum için bir `reloc` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8b17-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="d8b17-110">Bu, platforma bağlı olarak BASED_HIGHLOW veya BASED_DIR64 dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="d8b17-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="d8b17-111">32 bitlik bir sayının ilk 16 biti için bir `reloc` üretir, burada alt 16 bit,. reloc tablosundaki sonraki sözcüğe dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="d8b17-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="d8b17-112">Bir. reloc bölümüne hiçbir şey göndermek için bir belirteç eşlemesi konum değişikliği üretir.</span><span class="sxs-lookup"><span data-stu-id="d8b17-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="d8b17-113">Değerin bir göreli adres düzeltmesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8b17-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="d8b17-114">Bir. reloc bölümüne hiçbir şey göndermek için yalnızca bölüm göreli bir `reloc`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8b17-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="d8b17-115">Bu `reloc`, bölümün sanal adresini değil, bölümün dosya konumuyla ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="d8b17-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="d8b17-116">Kod göreli bir adres düzeltmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8b17-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="d8b17-117">IA64 `movl` yönergesinde 64 bitlik bir adres için `reloc` üretir.</span><span class="sxs-lookup"><span data-stu-id="d8b17-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="d8b17-118">64 bitlik bir adres için `reloc` üretir.</span><span class="sxs-lookup"><span data-stu-id="d8b17-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="d8b17-119">IA64 `br.call` yönergesinde 25 bit bılgısayar göreli adresi için `reloc` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d8b17-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="d8b17-120">IA64 `brl.call` yönergesinde 64 bitlik bılgısayar göreli adresi için bir `reloc` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8b17-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="d8b17-121">Etiketli işaretçi değerleri için kullanılan 30 bitlik bölüm göreli `reloc`üretir.</span><span class="sxs-lookup"><span data-stu-id="d8b17-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="d8b17-122">Bu sabit listesine yapılan eklerin iç `reloc` adı dizisine yansıtıldığından emin olmak için Sentinel değeri.</span><span class="sxs-lookup"><span data-stu-id="d8b17-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="d8b17-123">Temel `reloc`yaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8b17-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="d8b17-124">Bellek ön düzeltme içeriğinin, Bölüm boşluğu yerine bir işaretçi olduğunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="d8b17-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8b17-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8b17-125">Requirements</span></span>  
 <span data-ttu-id="d8b17-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8b17-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8b17-127">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d8b17-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8b17-128">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d8b17-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8b17-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8b17-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b17-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8b17-130">See also</span></span>

- [<span data-ttu-id="d8b17-131">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d8b17-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="d8b17-132">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8b17-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="d8b17-133">AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8b17-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
