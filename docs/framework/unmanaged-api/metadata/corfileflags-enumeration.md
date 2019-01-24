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
ms.openlocfilehash: 8a614ad1bd9738c993775667ccd261a089e8b57a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624269"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="b5567-102">CorFileFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b5567-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="b5567-103">Bir çağrı içinde tanımlanan dosya türü tanımlayan değerleri içeren [Imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="b5567-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5567-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5567-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b5567-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b5567-105">Members</span></span>  
  
|<span data-ttu-id="b5567-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b5567-106">Member</span></span>|<span data-ttu-id="b5567-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5567-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="b5567-108">Dosya kaynak dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5567-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="b5567-109">Meta veri dosyası, büyük olasılıkla bir kaynak dosya içermiyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5567-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5567-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5567-110">Requirements</span></span>  
 <span data-ttu-id="b5567-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5567-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5567-112">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b5567-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b5567-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5567-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5567-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5567-114">See also</span></span>
- [<span data-ttu-id="b5567-115">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b5567-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
