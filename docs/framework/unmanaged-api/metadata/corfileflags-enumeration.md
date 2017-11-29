---
title: "CorFileFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileFlags
helpviewer_keywords: CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf123f734f73ecfe726a80099de6ec06b0ced06b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="2b560-102">CorFileFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2b560-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="2b560-103">Çağrı tanımlanan dosya türü açıklamak değerleri içeren [Imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="2b560-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b560-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b560-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2b560-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2b560-105">Members</span></span>  
  
|<span data-ttu-id="2b560-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2b560-106">Member</span></span>|<span data-ttu-id="2b560-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b560-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="2b560-108">Dosyanın kaynak dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b560-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="2b560-109">Kaynak dosya büyük olasılıkla, dosya meta veri içermiyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b560-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b560-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b560-110">Requirements</span></span>  
 <span data-ttu-id="2b560-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b560-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b560-112">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2b560-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2b560-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b560-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b560-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b560-114">See Also</span></span>  
 [<span data-ttu-id="2b560-115">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="2b560-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
