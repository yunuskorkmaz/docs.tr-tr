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
ms.openlocfilehash: 7ecc2f62a6bb8119b7fe06a82aea827a58d04ecb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441674"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="5ecc9-102">CorFileFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5ecc9-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="5ecc9-103">Çağrı tanımlanan dosya türü açıklamak değerleri içeren [Imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="5ecc9-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ecc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ecc9-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5ecc9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5ecc9-105">Members</span></span>  
  
|<span data-ttu-id="5ecc9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5ecc9-106">Member</span></span>|<span data-ttu-id="5ecc9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ecc9-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="5ecc9-108">Dosyanın kaynak dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ecc9-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="5ecc9-109">Kaynak dosya büyük olasılıkla, dosya meta veri içermiyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ecc9-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ecc9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ecc9-110">Requirements</span></span>  
 <span data-ttu-id="5ecc9-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ecc9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ecc9-112">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5ecc9-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5ecc9-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ecc9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ecc9-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ecc9-114">See Also</span></span>  
 [<span data-ttu-id="5ecc9-115">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5ecc9-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
