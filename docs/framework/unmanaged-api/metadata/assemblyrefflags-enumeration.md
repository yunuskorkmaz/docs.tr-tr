---
title: "AssemblyRefFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyRefFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyRefFlags
helpviewer_keywords: AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc64d03725df89eac91c85549e287eeb2510037c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="046a8-102">AssemblyRefFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="046a8-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="046a8-103">Bir derleme başvurusu özelliklerini açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="046a8-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="046a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="046a8-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="046a8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="046a8-105">Members</span></span>  
  
|<span data-ttu-id="046a8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="046a8-106">Member</span></span>|<span data-ttu-id="046a8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="046a8-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="046a8-108">Derleme başvurusu derlemenin yayımcı hakkında tam, bütün bilgi içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="046a8-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="046a8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="046a8-109">Requirements</span></span>  
 <span data-ttu-id="046a8-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="046a8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="046a8-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="046a8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="046a8-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="046a8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="046a8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="046a8-113">See Also</span></span>  
 [<span data-ttu-id="046a8-114">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="046a8-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="046a8-115">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="046a8-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="046a8-116">DefineAssemblyRef yöntemi</span><span class="sxs-lookup"><span data-stu-id="046a8-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
