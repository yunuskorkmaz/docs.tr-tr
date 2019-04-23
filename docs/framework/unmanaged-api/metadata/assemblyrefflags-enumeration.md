---
title: AssemblyRefFlags Numaralandırması
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc98b2421d23ffd6dfb716a8cc782b46a9d59ce0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128902"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="dde69-102">AssemblyRefFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="dde69-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="dde69-103">Bir bütünleştirilmiş kod başvurusu özellikleri açıklanmaktadır değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="dde69-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dde69-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="dde69-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dde69-105">Members</span></span>  
  
|<span data-ttu-id="dde69-106">Üye</span><span class="sxs-lookup"><span data-stu-id="dde69-106">Member</span></span>|<span data-ttu-id="dde69-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dde69-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="dde69-108">Bütünleştirilmiş kod başvurusu derlemenin yayımcı hakkında tam, bütün bilgileri içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dde69-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dde69-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dde69-109">Requirements</span></span>  
 <span data-ttu-id="dde69-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde69-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde69-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="dde69-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dde69-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dde69-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde69-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dde69-113">See also</span></span>

- [<span data-ttu-id="dde69-114">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="dde69-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="dde69-115">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dde69-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="dde69-116">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dde69-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
