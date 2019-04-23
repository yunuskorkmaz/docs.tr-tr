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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 076d5de3e9d1925e3a030fee4a06a89862105897
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159620"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="d5adc-102">CorFileFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d5adc-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="d5adc-103">Bir çağrı içinde tanımlanan dosya türü tanımlayan değerleri içeren [Imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="d5adc-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5adc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5adc-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d5adc-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d5adc-105">Members</span></span>  
  
|<span data-ttu-id="d5adc-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d5adc-106">Member</span></span>|<span data-ttu-id="d5adc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5adc-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="d5adc-108">Dosya kaynak dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5adc-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="d5adc-109">Meta veri dosyası, büyük olasılıkla bir kaynak dosya içermiyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5adc-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5adc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5adc-110">Requirements</span></span>  
 <span data-ttu-id="d5adc-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5adc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5adc-112">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d5adc-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d5adc-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5adc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5adc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5adc-114">See also</span></span>

- [<span data-ttu-id="d5adc-115">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d5adc-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
