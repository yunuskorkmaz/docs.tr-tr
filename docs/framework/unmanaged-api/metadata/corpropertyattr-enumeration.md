---
title: CorPropertyAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5fb70d530af24798636972de0a4d6280dbcb8f1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781637"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="7f5d4-102">CorPropertyAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7f5d4-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="7f5d4-103">Özellik meta verileri tanımlayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7f5d4-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f5d4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="7f5d4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7f5d4-105">Members</span></span>  
  
|<span data-ttu-id="7f5d4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7f5d4-106">Member</span></span>|<span data-ttu-id="7f5d4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f5d4-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="7f5d4-108">Özelliği özeldir ve adını açıklayan belirtir nasıl.</span><span class="sxs-lookup"><span data-stu-id="7f5d4-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="7f5d4-109">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7f5d4-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="7f5d4-110">Ortak dil çalışma zamanı meta veri özellik adı kodlama dahili API'lerde denetleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f5d4-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="7f5d4-111">Özelliği varsayılan değerine sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f5d4-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="7f5d4-112">Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="7f5d4-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f5d4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f5d4-113">Requirements</span></span>  
 <span data-ttu-id="7f5d4-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f5d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f5d4-115">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7f5d4-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7f5d4-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f5d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5d4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f5d4-117">See also</span></span>

- [<span data-ttu-id="7f5d4-118">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7f5d4-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
