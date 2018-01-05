---
title: "CorPEKind Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPEKind
helpviewer_keywords: CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 612c71db092e7a3474d262c1d601335a5f416791
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="a4d90-102">CorPEKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a4d90-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="a4d90-103">Taşınabilir yürütülebilir (PE) dosyasını tanımlamak değerleri çağrısından döndürülen içeren [Imetadataımport2::getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="a4d90-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d90-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4d90-104">Syntax</span></span>  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="a4d90-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a4d90-105">Members</span></span>  
  
|<span data-ttu-id="a4d90-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a4d90-106">Member</span></span>|<span data-ttu-id="a4d90-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4d90-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="a4d90-108">Bunun bir PE dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4d90-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="a4d90-109">Bu PE dosya yönetilen kodu yalnızca içerdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4d90-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="a4d90-110">Bu PE dosya Win32 çağrılar olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4d90-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="a4d90-111">Bu PE dosya bir 64-bit platformda çalıştırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4d90-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="a4d90-112">Bu PE dosyanın yerel kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4d90-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="a4d90-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="a4d90-113">pe32BitPreferred</span></span>|<span data-ttu-id="a4d90-114">Bu PE dosya platformdan bağımsız ve 32-bit ortamında yüklenmesini tercih gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4d90-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4d90-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4d90-115">Remarks</span></span>  
 <span data-ttu-id="a4d90-116">Bu değerlerin Bitsel bileşimlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4d90-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d90-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4d90-117">Requirements</span></span>  
 <span data-ttu-id="a4d90-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d90-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d90-119">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a4d90-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a4d90-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d90-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d90-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4d90-121">See Also</span></span>  
 [<span data-ttu-id="a4d90-122">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a4d90-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
