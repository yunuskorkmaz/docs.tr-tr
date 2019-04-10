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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8f830ca7e273b65dc9ec77566a02df6c32cd464
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202397"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="0e8fc-102">CorPEKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0e8fc-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="0e8fc-103">Çağrısından döndürülen bir taşınabilir yürütülebilir (PE) dosya açıklayan değerleri içeren [Imetadataımport2::getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="0e8fc-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e8fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e8fc-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0e8fc-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0e8fc-105">Members</span></span>  
  
|<span data-ttu-id="0e8fc-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0e8fc-106">Member</span></span>|<span data-ttu-id="0e8fc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e8fc-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="0e8fc-108">Bunun bir PE dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e8fc-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="0e8fc-109">Bu PE dosyası yalnızca yönetilen kod içerdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e8fc-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="0e8fc-110">Gösterir. Bu PE dosyası Win32 çağrısı yapar.</span><span class="sxs-lookup"><span data-stu-id="0e8fc-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="0e8fc-111">Bu PE dosyası bir 64-bit platformda çalıştırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e8fc-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="0e8fc-112">Bu PE dosyası yerel kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e8fc-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="0e8fc-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="0e8fc-113">pe32BitPreferred</span></span>|<span data-ttu-id="0e8fc-114">Bu PE dosyası platformdan bağımsız ve 32-bit ortamında yüklenmesini tercih gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e8fc-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e8fc-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e8fc-115">Remarks</span></span>  
 <span data-ttu-id="0e8fc-116">Bu değerleri bit düzeyinde bileşimlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e8fc-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e8fc-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e8fc-117">Requirements</span></span>  
 <span data-ttu-id="0e8fc-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e8fc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e8fc-119">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0e8fc-119">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="0e8fc-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0e8fc-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e8fc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e8fc-121">See also</span></span>

- [<span data-ttu-id="0e8fc-122">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="0e8fc-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
