---
description: 'Daha fazla bilgi edinin: AssemblyRefFlags numaralandırması'
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
ms.openlocfilehash: 1b33faf816194c8b386f34a63d885ba37c4329a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678918"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="78bfe-103">AssemblyRefFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="78bfe-103">AssemblyRefFlags Enumeration</span></span>

<span data-ttu-id="78bfe-104">Bir derleme başvurusunun özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="78bfe-104">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bfe-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="78bfe-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="78bfe-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="78bfe-106">Members</span></span>  
  
|<span data-ttu-id="78bfe-107">Üye</span><span class="sxs-lookup"><span data-stu-id="78bfe-107">Member</span></span>|<span data-ttu-id="78bfe-108">Description</span><span class="sxs-lookup"><span data-stu-id="78bfe-108">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="78bfe-109">Derleme başvurusunun, derlemenin yayımcısı hakkında tam, karma olmayan bilgiler içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="78bfe-109">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78bfe-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78bfe-110">Requirements</span></span>  

 <span data-ttu-id="78bfe-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78bfe-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78bfe-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="78bfe-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78bfe-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78bfe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78bfe-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78bfe-114">See also</span></span>

- [<span data-ttu-id="78bfe-115">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="78bfe-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="78bfe-116">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78bfe-116">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="78bfe-117">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78bfe-117">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
