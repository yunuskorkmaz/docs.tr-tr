---
title: CorNativeLinkFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: 1362efbf518310240ce665badc93810d1c0b9b89
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450195"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="aadf7-102">CorNativeLinkFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="aadf7-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="aadf7-103">Yerel kod bağlanırken bağlayıcı tarafından kullanılan bayrak değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aadf7-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aadf7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aadf7-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="aadf7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="aadf7-105">Members</span></span>  
  
|<span data-ttu-id="aadf7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="aadf7-106">Member</span></span>|<span data-ttu-id="aadf7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aadf7-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="aadf7-108">Bayrak olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aadf7-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="aadf7-109">Bir `setLastError` anahtar sözcüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="aadf7-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="aadf7-110">Bir `nomangle` anahtar sözcüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="aadf7-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="aadf7-111">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="aadf7-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aadf7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aadf7-112">Requirements</span></span>  
 <span data-ttu-id="aadf7-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aadf7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aadf7-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="aadf7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aadf7-115">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="aadf7-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aadf7-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aadf7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aadf7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aadf7-117">See also</span></span>

- [<span data-ttu-id="aadf7-118">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="aadf7-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
