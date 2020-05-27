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
ms.openlocfilehash: c8c2757e99b80204ad52e69a596d62c55c369965
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007422"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="9bb98-102">CorFileFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9bb98-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="9bb98-103">IMetaDataAssemblyEmit çağrısında tanımlanan dosya türünü tanımlayan değerleri içerir [::D efineFile](imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="9bb98-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bb98-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9bb98-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9bb98-105">Members</span></span>  
  
|<span data-ttu-id="9bb98-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9bb98-106">Member</span></span>|<span data-ttu-id="9bb98-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bb98-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="9bb98-108">Dosyanın bir kaynak dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bb98-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="9bb98-109">Dosyanın, muhtemelen bir kaynak dosyasında meta veri içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bb98-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bb98-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bb98-110">Requirements</span></span>  
 <span data-ttu-id="9bb98-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bb98-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bb98-112">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="9bb98-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9bb98-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bb98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb98-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bb98-114">See also</span></span>

- [<span data-ttu-id="9bb98-115">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="9bb98-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
