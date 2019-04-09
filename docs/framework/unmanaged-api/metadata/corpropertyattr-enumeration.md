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
ms.openlocfilehash: f1a0fff266e964b506b2dc7c4030caa54abaa5ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171827"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="aefd4-102">CorPropertyAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="aefd4-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="aefd4-103">Özellik meta verileri tanımlayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="aefd4-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aefd4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aefd4-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="aefd4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="aefd4-105">Members</span></span>  
  
|<span data-ttu-id="aefd4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="aefd4-106">Member</span></span>|<span data-ttu-id="aefd4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aefd4-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="aefd4-108">Özelliği özeldir ve adını açıklayan belirtir nasıl.</span><span class="sxs-lookup"><span data-stu-id="aefd4-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="aefd4-109">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="aefd4-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="aefd4-110">Ortak dil çalışma zamanı meta veri özellik adı kodlama dahili API'lerde denetleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aefd4-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="aefd4-111">Özelliği varsayılan değerine sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="aefd4-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="aefd4-112">Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="aefd4-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aefd4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aefd4-113">Requirements</span></span>  
 <span data-ttu-id="aefd4-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aefd4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aefd4-115">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="aefd4-115">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="aefd4-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="aefd4-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aefd4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aefd4-117">See also</span></span>

- [<span data-ttu-id="aefd4-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="aefd4-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
