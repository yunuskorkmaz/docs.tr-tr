---
title: CorPEKind Numaralandırması
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 001be0c5e8897bacf76d2a044fb9400768473052
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673547"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="34b0d-102">CorPEKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="34b0d-102">CorPEKind Enumeration</span></span>

<span data-ttu-id="34b0d-103">[IMetaDataImport2:: GetPEKind](imetadataimport2-getpekind-method.md)çağrısından döndürülen bir taşınabilir YÜRÜTÜLEBILIR (PE) dosyasını tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="34b0d-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34b0d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="34b0d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="34b0d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="34b0d-105">Members</span></span>  
  
|<span data-ttu-id="34b0d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="34b0d-106">Member</span></span>|<span data-ttu-id="34b0d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34b0d-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="34b0d-108">Bunun bir PE dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="34b0d-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="34b0d-109">Bu PE dosyasının yalnızca yönetilen kod içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="34b0d-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="34b0d-110">Bu PE dosyasının Win32 çağrıları yaptığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="34b0d-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="34b0d-111">Bu PE dosyasının 64 bitlik bir platformda çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="34b0d-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="34b0d-112">Bu PE dosyasının yerel kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="34b0d-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="34b0d-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="34b0d-113">pe32BitPreferred</span></span>|<span data-ttu-id="34b0d-114">Bu PE dosyasının platformdan bağımsız olduğunu ve 32 bitlik bir ortamda yüklenmesinin tercih edildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="34b0d-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34b0d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34b0d-115">Remarks</span></span>  

 <span data-ttu-id="34b0d-116">Bu değerler bit düzeyinde kombinasyonlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="34b0d-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34b0d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34b0d-117">Requirements</span></span>  

 <span data-ttu-id="34b0d-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34b0d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34b0d-119">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="34b0d-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="34b0d-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34b0d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b0d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34b0d-121">See also</span></span>

- [<span data-ttu-id="34b0d-122">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="34b0d-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
