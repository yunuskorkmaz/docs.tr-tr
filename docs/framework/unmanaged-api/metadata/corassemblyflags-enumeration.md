---
description: 'Daha fazla bilgi edinin: CorAssemblyFlags sabit listesi'
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
ms.openlocfilehash: bd74534b1f607eea15f1d8615f66723428ddae3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678496"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="cb24a-103">CorAssemblyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cb24a-103">CorAssemblyFlags Enumeration</span></span>

<span data-ttu-id="cb24a-104">Bir derleme derlemesine uygulanan meta verileri tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-104">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb24a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb24a-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cb24a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cb24a-106">Members</span></span>  
  
|<span data-ttu-id="cb24a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="cb24a-107">Member</span></span>|<span data-ttu-id="cb24a-108">Description</span><span class="sxs-lookup"><span data-stu-id="cb24a-108">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="cb24a-109">Derleme başvurusunun tam, karma olmayan ortak anahtarı tuttuğunda olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-109">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="cb24a-110">İşlemci mimarisinin belirtilmemiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-110">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="cb24a-111">İşlemci mimarisinin nötr (PE32) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-111">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="cb24a-112">İşlemci mimarisinin x86 (PE32) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-112">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="cb24a-113">İşlemci mimarisinin Itanium (PE32 +) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-113">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="cb24a-114">İşlemci mimarisinin AMD x64 (PE32 +) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-114">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="cb24a-115">İşlemci mimarisinin ARM (PE32) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-115">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="cb24a-116">Derlemenin bir başvuru derlemesi olduğunu belirtir; diğer bir deyişle, her türlü mimari için geçerlidir, ancak herhangi bir mimaride çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="cb24a-116">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="cb24a-117">Bu nedenle, bayrak ile aynıdır `afPA_Mask` .</span><span class="sxs-lookup"><span data-stu-id="cb24a-117">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="cb24a-118">İşlemci mimarisi bayraklarının kayda yayıldığını gösterir `AssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="cb24a-118">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="cb24a-119">İşlemci mimarisini tanımlayan bir maske.</span><span class="sxs-lookup"><span data-stu-id="cb24a-119">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="cb24a-120">İşlemci mimarisi açıklamasının dahil edildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-120">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="cb24a-121">Dizin ve dizinden gelen işlemci mimarisi bayraklarının bir kaydırma sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-121">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="cb24a-122">Öğesinden karşılık gelen değeri gösterir <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cb24a-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="cb24a-123">Öğesinden karşılık gelen değeri gösterir <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cb24a-123">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="cb24a-124">Derlemenin çalışma zamanında farklı bir yayımcıdan bir derlemeye yeniden hedeflenebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-124">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="cb24a-125">İçerik türünü tanımlayan bir maske.</span><span class="sxs-lookup"><span data-stu-id="cb24a-125">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="cb24a-126">Varsayılan içerik türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-126">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="cb24a-127">Windows Çalışma Zamanı içerik türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb24a-127">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb24a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb24a-128">Requirements</span></span>  

 <span data-ttu-id="cb24a-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb24a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb24a-130">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="cb24a-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cb24a-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb24a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb24a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb24a-132">See also</span></span>

- [<span data-ttu-id="cb24a-133">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="cb24a-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
