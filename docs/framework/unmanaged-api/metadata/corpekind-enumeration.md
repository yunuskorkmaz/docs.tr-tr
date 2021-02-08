---
description: 'Daha fazla bilgi edinin: CorPEKind numaralandırması'
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
ms.openlocfilehash: 6d1f29a220ce9d4be4151d8eff6557fa8c693ed2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784281"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="72b8d-103">CorPEKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="72b8d-103">CorPEKind Enumeration</span></span>

<span data-ttu-id="72b8d-104">[IMetaDataImport2:: GetPEKind](imetadataimport2-getpekind-method.md)çağrısından döndürülen bir taşınabilir YÜRÜTÜLEBILIR (PE) dosyasını tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="72b8d-104">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b8d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="72b8d-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="72b8d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="72b8d-106">Members</span></span>  
  
|<span data-ttu-id="72b8d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="72b8d-107">Member</span></span>|<span data-ttu-id="72b8d-108">Description</span><span class="sxs-lookup"><span data-stu-id="72b8d-108">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="72b8d-109">Bunun bir PE dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="72b8d-109">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="72b8d-110">Bu PE dosyasının yalnızca yönetilen kod içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="72b8d-110">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="72b8d-111">Bu PE dosyasının Win32 çağrıları yaptığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="72b8d-111">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="72b8d-112">Bu PE dosyasının 64 bitlik bir platformda çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="72b8d-112">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="72b8d-113">Bu PE dosyasının yerel kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="72b8d-113">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="72b8d-114">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="72b8d-114">pe32BitPreferred</span></span>|<span data-ttu-id="72b8d-115">Bu PE dosyasının platformdan bağımsız olduğunu ve 32 bitlik bir ortamda yüklenmesinin tercih edildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72b8d-115">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72b8d-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72b8d-116">Remarks</span></span>  

 <span data-ttu-id="72b8d-117">Bu değerler bit düzeyinde kombinasyonlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="72b8d-117">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72b8d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72b8d-118">Requirements</span></span>  

 <span data-ttu-id="72b8d-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72b8d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72b8d-120">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="72b8d-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="72b8d-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72b8d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b8d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72b8d-122">See also</span></span>

- [<span data-ttu-id="72b8d-123">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="72b8d-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
