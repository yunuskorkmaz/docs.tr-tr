---
title: "AssemblyRefFlags Numaralandırması"
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
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0a749a2f0016e7f2ea22c1d61c82f25ac78a9b9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="a8d6b-102">AssemblyRefFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a8d6b-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="a8d6b-103">Bir derleme başvurusu özelliklerini açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a8d6b-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d6b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8d6b-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a8d6b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a8d6b-105">Members</span></span>  
  
|<span data-ttu-id="a8d6b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a8d6b-106">Member</span></span>|<span data-ttu-id="a8d6b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8d6b-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="a8d6b-108">Derleme başvurusu derlemenin yayımcı hakkında tam, bütün bilgi içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8d6b-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8d6b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8d6b-109">Requirements</span></span>  
 <span data-ttu-id="a8d6b-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8d6b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d6b-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a8d6b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8d6b-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8d6b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d6b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8d6b-113">See Also</span></span>  
 [<span data-ttu-id="a8d6b-114">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a8d6b-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="a8d6b-115">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8d6b-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="a8d6b-116">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d6b-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
