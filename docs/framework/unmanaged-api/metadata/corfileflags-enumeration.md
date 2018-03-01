---
title: "CorFileFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 939c7997849adfed090ead3b197c690e0202f37c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="26373-102">CorFileFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="26373-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="26373-103">Çağrı tanımlanan dosya türü açıklamak değerleri içeren [Imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="26373-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26373-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26373-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="26373-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="26373-105">Members</span></span>  
  
|<span data-ttu-id="26373-106">Üye</span><span class="sxs-lookup"><span data-stu-id="26373-106">Member</span></span>|<span data-ttu-id="26373-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26373-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="26373-108">Dosyanın kaynak dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26373-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="26373-109">Kaynak dosya büyük olasılıkla, dosya meta veri içermiyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="26373-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26373-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26373-110">Requirements</span></span>  
 <span data-ttu-id="26373-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26373-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26373-112">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="26373-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="26373-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26373-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26373-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26373-114">See Also</span></span>  
 [<span data-ttu-id="26373-115">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="26373-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
