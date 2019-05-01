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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eca4b66a3f7c1a96bb06827dde477f34cb904ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906249"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="ec92c-102">CorAssemblyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ec92c-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="ec92c-103">Bir derleme derlemeye uygulanan meta verileri tanımlayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec92c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec92c-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="ec92c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ec92c-105">Members</span></span>  
  
|<span data-ttu-id="ec92c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ec92c-106">Member</span></span>|<span data-ttu-id="ec92c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec92c-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="ec92c-108">Bütünleştirilmiş kod başvurusu tam, bütün ortak anahtarı saklar gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="ec92c-109">İşlemci mimarisi belirtilmeyen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="ec92c-110">İşlemci mimarisi nötr olduğunu gösterir (PE32).</span><span class="sxs-lookup"><span data-stu-id="ec92c-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="ec92c-111">İşlemci mimarisi x86 (PE32) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="ec92c-112">İşlemci mimarisi Itanium (PE32 +) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="ec92c-113">İşlemci mimarisi AMD X64 (PE32 +) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="ec92c-114">İşlemci mimarisi ARM (PE32) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="ec92c-115">Derlemeye bir başvuru bütünleştirilmiş kodu olduğunu gösterir; diğer bir deyişle, tüm mimarisi için geçerlidir ancak herhangi bir mimari üzerinde çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="ec92c-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="ec92c-116">Bu nedenle, bayrağı aynıdır `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="ec92c-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="ec92c-117">İşlemci mimarisi bayrakları için dağıtılmasını belirten `AssemblyRef` kaydı.</span><span class="sxs-lookup"><span data-stu-id="ec92c-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="ec92c-118">İşlemci mimarisini açıklar maskesi.</span><span class="sxs-lookup"><span data-stu-id="ec92c-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="ec92c-119">İşlemci mimarisi açıklaması dahil olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="ec92c-120">Bir kaydırma sayısı İşlemci mimarisi bayrakları dizini gelen ve giden olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="ec92c-121">Karşılık gelen değeri gösteren <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> , <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ec92c-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="ec92c-122">Karşılık gelen değeri gösteren <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> , <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ec92c-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="ec92c-123">Derleme çalışma zamanında bir derlemeye farklı bir yayımcı tarafından hedeflenmesi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="ec92c-124">İçerik türünü açıklayan maskesi.</span><span class="sxs-lookup"><span data-stu-id="ec92c-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="ec92c-125">Varsayılan içerik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec92c-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="ec92c-126">Gösterir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] içerik türü.</span><span class="sxs-lookup"><span data-stu-id="ec92c-126">Indicates the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec92c-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec92c-127">Requirements</span></span>  
 <span data-ttu-id="ec92c-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec92c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec92c-129">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ec92c-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ec92c-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec92c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec92c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec92c-131">See also</span></span>

- [<span data-ttu-id="ec92c-132">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ec92c-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
