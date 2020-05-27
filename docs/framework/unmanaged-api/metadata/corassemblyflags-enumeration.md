---
title: CorAssemblyFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: b1a83f07f03ddb17d5c306453cf838101a77ed65
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007942"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="74e0e-102">CorAssemblyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="74e0e-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="74e0e-103">Bir derleme derlemesine uygulanan meta verileri tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74e0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74e0e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="74e0e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="74e0e-105">Members</span></span>  
  
|<span data-ttu-id="74e0e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="74e0e-106">Member</span></span>|<span data-ttu-id="74e0e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74e0e-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="74e0e-108">Derleme başvurusunun tam, karma olmayan ortak anahtarı tuttuğunda olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="74e0e-109">İşlemci mimarisinin belirtilmemiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="74e0e-110">İşlemci mimarisinin nötr (PE32) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="74e0e-111">İşlemci mimarisinin x86 (PE32) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="74e0e-112">İşlemci mimarisinin Itanium (PE32 +) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="74e0e-113">İşlemci mimarisinin AMD x64 (PE32 +) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="74e0e-114">İşlemci mimarisinin ARM (PE32) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="74e0e-115">Derlemenin bir başvuru derlemesi olduğunu belirtir; diğer bir deyişle, her türlü mimari için geçerlidir, ancak herhangi bir mimaride çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="74e0e-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="74e0e-116">Bu nedenle, bayrak ile aynıdır `afPA_Mask` .</span><span class="sxs-lookup"><span data-stu-id="74e0e-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="74e0e-117">İşlemci mimarisi bayraklarının kayda yayıldığını gösterir `AssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="74e0e-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="74e0e-118">İşlemci mimarisini tanımlayan bir maske.</span><span class="sxs-lookup"><span data-stu-id="74e0e-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="74e0e-119">İşlemci mimarisi açıklamasının dahil edildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="74e0e-120">Dizin ve dizinden gelen işlemci mimarisi bayraklarının bir kaydırma sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="74e0e-121">Öğesinden karşılık gelen değeri gösterir <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="74e0e-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="74e0e-122">Öğesinden karşılık gelen değeri gösterir <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="74e0e-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="74e0e-123">Derlemenin çalışma zamanında farklı bir yayımcıdan bir derlemeye yeniden hedeflenebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="74e0e-124">İçerik türünü tanımlayan bir maske.</span><span class="sxs-lookup"><span data-stu-id="74e0e-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="74e0e-125">Varsayılan içerik türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="74e0e-126">Windows Çalışma Zamanı içerik türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e0e-126">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74e0e-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74e0e-127">Requirements</span></span>  
 <span data-ttu-id="74e0e-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74e0e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74e0e-129">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="74e0e-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="74e0e-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e0e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e0e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74e0e-131">See also</span></span>

- [<span data-ttu-id="74e0e-132">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="74e0e-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
