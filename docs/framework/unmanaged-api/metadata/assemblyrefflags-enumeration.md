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
ms.openlocfilehash: 1307f555c9d8b6d28febcf25db89ae856c143d71
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009411"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="e9663-102">AssemblyRefFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e9663-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="e9663-103">Bir derleme başvurusunun özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e9663-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9663-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9663-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e9663-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e9663-105">Members</span></span>  
  
|<span data-ttu-id="e9663-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e9663-106">Member</span></span>|<span data-ttu-id="e9663-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9663-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="e9663-108">Derleme başvurusunun, derlemenin yayımcısı hakkında tam, karma olmayan bilgiler içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9663-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9663-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9663-109">Requirements</span></span>  
 <span data-ttu-id="e9663-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9663-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9663-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e9663-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9663-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9663-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9663-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9663-113">See also</span></span>

- [<span data-ttu-id="e9663-114">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="e9663-114">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="e9663-115">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9663-115">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="e9663-116">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9663-116">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
