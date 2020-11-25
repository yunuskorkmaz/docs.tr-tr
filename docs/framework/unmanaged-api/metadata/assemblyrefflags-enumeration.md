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
ms.openlocfilehash: 0a99d2f79645bdc46ff4db86d7280614eeb1faf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732768"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="24d23-102">AssemblyRefFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="24d23-102">AssemblyRefFlags Enumeration</span></span>

<span data-ttu-id="24d23-103">Bir derleme başvurusunun özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="24d23-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24d23-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="24d23-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="24d23-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="24d23-105">Members</span></span>  
  
|<span data-ttu-id="24d23-106">Üye</span><span class="sxs-lookup"><span data-stu-id="24d23-106">Member</span></span>|<span data-ttu-id="24d23-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24d23-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="24d23-108">Derleme başvurusunun, derlemenin yayımcısı hakkında tam, karma olmayan bilgiler içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="24d23-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24d23-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24d23-109">Requirements</span></span>  

 <span data-ttu-id="24d23-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24d23-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24d23-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="24d23-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24d23-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24d23-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d23-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24d23-113">See also</span></span>

- [<span data-ttu-id="24d23-114">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="24d23-114">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="24d23-115">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24d23-115">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="24d23-116">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24d23-116">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
