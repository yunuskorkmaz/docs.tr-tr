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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e6eb2a30dd6722309fd80c1611ad9200ab14ae5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152002"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="bfa83-102">CorNativeLinkFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bfa83-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="bfa83-103">Bağlayıcı tarafından yerel kod bağlanırken kullanılan bayrak değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfa83-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfa83-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfa83-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bfa83-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bfa83-105">Members</span></span>  
  
|<span data-ttu-id="bfa83-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bfa83-106">Member</span></span>|<span data-ttu-id="bfa83-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfa83-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="bfa83-108">Hiçbir bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfa83-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="bfa83-109">Belirten bir `setLastError` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bfa83-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="bfa83-110">Belirten bir `nomangle` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bfa83-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="bfa83-111">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="bfa83-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bfa83-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfa83-112">Requirements</span></span>  
 <span data-ttu-id="bfa83-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfa83-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfa83-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bfa83-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bfa83-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bfa83-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="bfa83-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bfa83-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bfa83-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfa83-117">See also</span></span>

- [<span data-ttu-id="bfa83-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bfa83-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
