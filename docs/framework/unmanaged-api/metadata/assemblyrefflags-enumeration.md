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
ms.openlocfilehash: c402dcda79f013b19b091c6309b3d71951018a18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776360"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="38205-102">AssemblyRefFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="38205-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="38205-103">Bir bütünleştirilmiş kod başvurusu özellikleri açıklanmaktadır değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="38205-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38205-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38205-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="38205-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="38205-105">Members</span></span>  
  
|<span data-ttu-id="38205-106">Üye</span><span class="sxs-lookup"><span data-stu-id="38205-106">Member</span></span>|<span data-ttu-id="38205-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38205-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="38205-108">Bütünleştirilmiş kod başvurusu derlemenin yayımcı hakkında tam, bütün bilgileri içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38205-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38205-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38205-109">Requirements</span></span>  
 <span data-ttu-id="38205-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38205-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38205-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="38205-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38205-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38205-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38205-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38205-113">See also</span></span>

- [<span data-ttu-id="38205-114">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="38205-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="38205-115">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38205-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="38205-116">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38205-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
