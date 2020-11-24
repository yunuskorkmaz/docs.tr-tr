---
title: CorFileFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: 70d789f417700734b546cac6ff527ed5aa84fcf9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688633"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="96dd7-102">CorFileFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="96dd7-102">CorFileFlags Enumeration</span></span>

<span data-ttu-id="96dd7-103">IMetaDataAssemblyEmit çağrısında tanımlanan dosya türünü tanımlayan değerleri içerir [::D efineFile](imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="96dd7-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96dd7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="96dd7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="96dd7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="96dd7-105">Members</span></span>  
  
|<span data-ttu-id="96dd7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="96dd7-106">Member</span></span>|<span data-ttu-id="96dd7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96dd7-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="96dd7-108">Dosyanın bir kaynak dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96dd7-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="96dd7-109">Dosyanın, muhtemelen bir kaynak dosyasında meta veri içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="96dd7-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96dd7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96dd7-110">Requirements</span></span>  

 <span data-ttu-id="96dd7-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96dd7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96dd7-112">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="96dd7-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="96dd7-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96dd7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96dd7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96dd7-114">See also</span></span>

- [<span data-ttu-id="96dd7-115">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="96dd7-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
